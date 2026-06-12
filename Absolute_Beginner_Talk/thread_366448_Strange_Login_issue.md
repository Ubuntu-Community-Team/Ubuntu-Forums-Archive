---
title: "Strange Login issue"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Quinton007 on 2007-02-20
I used the dpkg-reconfigure xserver-xorg to set up the fglrx driver for my ATI X700 pro.  This caused my login screen to disappear (or more so to not send a signal to my monitor, because I can still login by typing my username and password).  Also this has now disabled my sound.  Please help

---

### Post by dcstar on 2007-02-20
> **Quinton007 said:**
> I used the dpkg-reconfigure xserver-xorg to set up the fglrx driver for my ATI X700 pro.  This caused my login screen to disappear (or more so to not send a signal to my monitor, because I can still login by typing my username and password).  Also this has now disabled my sound.  Please help

Press CTRL-ALT-F1, log into the text screen as normal, then repeat the **sudo dpkg-reconfigure xserver-xorg** process and select the VESA driver, then:
```
sudo /etc/init.d/gdm restart
``` and you should have a working system again.

Then you can try and figure out why the other driver didn't work.

---

### Post by Quinton007 on 2007-02-20
Swapping back to the vesa denied any sort of GUI.  It didn't allow me to start over.

---

