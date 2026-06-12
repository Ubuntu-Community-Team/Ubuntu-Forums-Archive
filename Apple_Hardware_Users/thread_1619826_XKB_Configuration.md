---
title: "XKB Configuration"
date: 2010-11-12
forum: Apple Hardware Users
---

### Post by idealistic on 2010-11-12
Hi,

I have a macbook 2,1 with Maverick 10.10.
recently everytime i start a session or when i start the computer i get this :

Error activating XKB configuration.
It can happen under various circumstances:
 • a bug in libxklavier library
 • a bug in X server (xkbcomp, xmodmap utilities)
 • X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10900000

If you report this situation as a bug, please include:
 • The result of xprop -root | grep XKB
 • The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

and then : 

theo@theo-laptop:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "fr", "mac", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "fr", "mac", ""
theo@theo-laptop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [fr    mac]
 options = [grp    grp:alts_toggle,japan    japan:kana_lock]
 model = macbook78

i don't understand anything, can somebody explain to me how to fix this ?

Thanks

---

### Post by linuxopjemac on 2010-11-12
known bug
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/596652](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/596652)

try changing keyboard layout from "USA (Macintosh)" to "US"

---

