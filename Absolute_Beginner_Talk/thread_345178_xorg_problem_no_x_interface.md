---
title: "xorg problem: no x interface"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by caltabellotta on 2007-01-23
Ok, I was trying (again) to up my laptop resolution from 1024x768 to 1200x800.  I added this line into xorg.conf, therefore causing it to crash:

```
Modes "1280x800" "800x600" "640x480"
```

Now I cannot login to ubuntu because of this display error.  I cannot figure out how to delete my errors through recovery.  Any help would be great........

Calta

---

### Post by rabid emu on 2007-01-23
boot into recovery mode.  type 'dpkg-reconfigure xserver-xorg' and it'll reset your xserver settings to defaults (based on a few prompts that can mostly be left to defaults).

A good idea, before messing with xorg, is to make sure you have a correct driver for your graphics card installed.  Once it is, you should be able to select the proper resolution from the gui easily.

---

### Post by bionnaki on 2007-01-24
...and always back up what you cannot undo.

always do this before messing with your xorg.conf:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

and to restore the working xorg.conf, do the following

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

and then restart x

---

