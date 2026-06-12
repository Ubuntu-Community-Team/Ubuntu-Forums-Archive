---
title: "error message on startup"
date: 2008-08-09
forum: Apple Hardware Users
---

### Post by jeh0753 on 2008-08-09
The following error message appears on startup:
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Results of these commands:
```
jeh0753@jake:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
jeh0753@jake:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = macbook78
 overrideSettings = true
 options = []
jeh0753@jake:~$ 

```
What might I do to stop this from appearing?

---

