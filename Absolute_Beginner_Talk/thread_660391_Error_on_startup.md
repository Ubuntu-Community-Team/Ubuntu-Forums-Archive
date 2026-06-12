---
title: "Error on startup"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Fleece Flamingo on 2008-01-06
I get this error and my windows don't have any close, minimize etc...
I already checked my windows decorations and it's checked.
My screen doesn't seem to be displaying properly either I get a white blank spot on the bottom part of my screen. 

[[IMG]http://img106.imageshack.us/img106/8733/screenshotfk4.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotfk4.png)

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

My keyboard super button doesn't seem to be working either.

---

### Post by Blutack on 2008-01-06
This a new install or sudden bug?
You can reinitialise the XKB config by running
sudo dpkg-reconfigure -phigh xserver-xorg
see if that does the trick.

---

### Post by Fleece Flamingo on 2008-01-06
This is just a random bug, everything was good until now.

---

### Post by Fleece Flamingo on 2008-01-06
I just tried to open my terminal and it isn't appearing, just shows as a white box.
How do I do the full screen terminal?

---

### Post by Fleece Flamingo on 2008-01-06
Whatever I am just going to do a reinstall.

---

