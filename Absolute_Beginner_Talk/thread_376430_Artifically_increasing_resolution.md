---
title: "Artifically increasing resolution"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by qiemem on 2007-03-04
Kind of an odd question here... Is there anyway to artificially increase screen resolution? My screen maxes out at 1024x768 (older laptop), and its a little frustratingly small. So is there anyway to shrink everything on screen as though I was running at a higher resolution?
Thanks!

---

### Post by taurus on 2007-03-04
Just edit /etc/X11/xorg.conf

Applications -> Accessories -> Terminal
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```
and remove whatever resolutions you don't want to use.  Leave the one you want to use at the beginning.

Save it and reboot.

---

### Post by igknighted on 2007-03-04
You could go through and manually change font size/icons size/panel size etc., that would give that appearance I would imagine.

---

