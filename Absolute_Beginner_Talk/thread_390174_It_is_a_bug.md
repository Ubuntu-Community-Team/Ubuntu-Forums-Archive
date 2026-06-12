---
title: "It is a bug?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by gingin on 2007-03-21
[COLOR="Black"][/COLOR]

I getting such message just after system boot. Is ita bug?

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by fakie_flip on 2007-03-21
Report it to launchpad with the output of those commands.

xprop -root | grep XKB
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by gingin on 2007-03-21
Thks just did that.

---

