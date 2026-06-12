---
title: "error when selecting (assumed) best keyboard layout for macbook"
date: 2007-06-04
forum: Apple Intel Users
---

### Post by Zelut on 2007-06-04
Yesterday I was delving into selecting the proper keyboard layout for my MacBook via the gnome "System > Preferences > Keyboard".  By default it had listed "Generic 105-key (Intl) PC".  I'm assuming a better selection would be the "MacBook/MacBook Pro" selection, but when I select that (or select anything for that matter) I get the following error:

> 
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


Is this something that should be bug reported on LP or is this fixable based on someones experience?  Let me know, thank you.

---

### Post by ronocdh on 2007-06-05
I have only ever changed keyboard settings by using **sudo dpkg-reconfigure xserver-xorg**. If the GNOME panel is giving you problems, report it. I believe the keyboard I was using was US Macintosh or something like that. Never have had any problems.

---

