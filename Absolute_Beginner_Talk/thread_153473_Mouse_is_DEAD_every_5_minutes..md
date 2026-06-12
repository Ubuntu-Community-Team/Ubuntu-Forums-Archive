---
title: "Mouse is DEAD every 5 minutes."
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by Adramelech on 2006-04-01
This is driving me nuts I cant stand the mouse being useless every 5 minutes, it freezes, is a usb mouse and my kernel is up to date, mouse didnt behave like this, maybe is the new kernel, how do i go back to an old kernel? the only way i found to enable the mouse again is "modprobe mouse" and it says "FATAL: Module mouse not found" i really dont know if is supposed to exist but this line is only way i found to enable my mouse for another 5 minutes withour restarting X.

---

### Post by Pragmatist on 2006-04-02
Send us your /etc/X11/xorg.conf file.  It is a big file, so append it if possible.  If you need to work without the mouse while doing that, just go into a VT by typing CTRL-ALT-F4 and then logging in. Instead of F4 you could also use F1 F2 F3 F5 or F6  but some of these will be unavailable.  Now you are in a text terminal.  To go back to your graphical environment, just type CTRL-ALT-F7

---

