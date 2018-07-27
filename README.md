# fvwm95
---
This is a fork of fvwm95 meant to be compilable on and play nice with newer versions of Debian (and possibly Ubuntu and other distros, needs testing).

It is based off the code from the source package in Debian Sarge, slightly modified so that it compiles without errors on modern Debian, and with a more sane configuration to adapt to modern day needs.

![Reference screenshot](/screenshot.png?raw=true "Reference screenshot")

## How to build
The following packages are needed in order to build fvwm95 on Debian:
* xorg
* build-essential
* libx11-dev
* libxt-dev
* libxext-dev
* libxpm-dev
* libreadline-dev
* libxmu-headers
* bison
* flex
* autoconf

The following packages are not necessary to build fvwm95 itself, but
they are recommended to have:

* xscreensaver
* nitrogen
* thunar
* xterm
* lxappearance
* pulseaudio
* pavucontrol

## Switching locales

Sadly, fvwm95 does not seem to support UTF-8 locales at all, therefore, in order to run it, you'll have to switch to a ISO-8859-1 locale.

**This is something you might want to avoid, so think twice before deciding to install fvwm95 on a production machine.**

---
To switch to a ISO-8859-1 locale on Debian, edit the file `/etc/locale.gen` (as root).

In this file, comment out any UTF-8 lines corresponding to your locale, and uncomment the ones that specify `ISO-8859-1`.

For instance, assuming the locale you use is en_US:

Find
```en_US.UTF-8 UTF-8 ```
and make it into
```# en_US.UTF-8 UTF-8 ```.

Then, find
```# en_US ISO-8859-1 ```
and make it into
```en_US ISO-8859-1 ```.

Once that's done, save the file, then run:
```
sudo locale-gen
```

**You must now log out and back in to apply these settings, or simply reboot.**

## Actually installing
After all the dependencies are satisfied, configure, build, and
install fvwm95 by running:
```
./configure --prefix=/usr/local
make
sudo make install
```

In order to start fvwm95 with xinit, add the following to your
`~/.xinitrc` file:
```
exec fvwm95
```

To start it, simply type:
```
startx
```

Enjoy!