---
title: "SERIOUS problem with Spanish keyboard (laptop)"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-18
Hi all,

I have a Toshiba A30-714 with a Spanish keyboard layout. I have never had any issues with keyboards not working under Ubuntu, but recently I have been 'messing around' in that xserver-xorg business through the terminal (sudo dpkg-reconfigure xserver-xorg), in a vauge attempt to get multiple montors working...

However, that failed, but I remember that at a certain stage it asks about keyboards - and since then it has stopped working, in that the Alt Gr keys don't function (or special characters). If I try to change a setting in "keyboards" (under "Preferences"), I get the following error message...

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


Any ideas anyone? I have no idea how I've screwed this up.

---

### Post by szofiel on 2006-08-30
Curious, I have the same trouble, but with a lightly differente approach: does any knows how to roll back Gnome keyboard control instead of Xorg?

It was an option right at the beginning of the session, wich I did change to permanent, instead of the temporary option, but would like to get it back.

Anybody?...

---

