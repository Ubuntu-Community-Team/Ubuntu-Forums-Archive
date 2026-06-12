---
title: "Requesting correct Xorg and Gnome settings for new apple aluminium keyboards"
date: 2007-10-30
forum: Apple Intel Users
---

### Post by Tech^CF on 2007-10-30
I have been having some trouble with my aluminium Apple keyboard. Hotkeys binded to F13-19 doesn't work. After fiddling around, I seem to have broken configuration as I get this upon login:

```
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

Xprop says:

```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "no", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "apple", "no", "mac", "lv3:ralt_switch"

```

Gconftool says:
```
layouts = []
 model = macintosh
 overrideSettings = true
 options = []

```

---

### Post by cyberdork33 on 2007-10-30
well F13 - F19 are not on most standard keyboards, and that is likely the reason you are having problems. Also, since you have one of the new apple keyboards, they may not be detected properly yet, giving your the strange error. 

Have you tried [keytouch]("http://keytouch.sourceforge.net/")?

If you want to report a bug, this is not the place to do it. Try here:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by Tech^CF on 2007-10-30
Thanks for the tip about keytouch.

I have had the keyboard work earlier (when testing Kubuntu 7.10) - So it should be possible to get it to work in Ubuntu too. I just don't know what the correct values in xorg.conf is and what the gnome settings should be.

It is propably not a bug.

---

### Post by FunkyM on 2007-10-30
The aluminum keyboards extended features are supported just lately.

Kernel patches are available here (check the two):
 [http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=shortlog;h=upstream](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=shortlog;h=upstream)

---

