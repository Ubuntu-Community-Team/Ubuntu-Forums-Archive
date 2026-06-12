---
title: "Ubuntu Studio No Xorg"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2008-02-28
Ok so I installed from the Studio 7.10 64 bit CD and I booted up, but there is no X at all what do I do.  I cannot write my own Xorg cause I have no idea where to start.  I put in X command, and it tells me that the Xorg does not exist, so X is valid, but no .conf file was written.

Is there an xorg creator command, I forgot my text commands for X.

---

### Post by madmatrixz3000 on 2008-02-28
Bump

---

### Post by SOULRiDER on 2008-02-28
Try 
```
sudo dpkg-reconfigure xserver-xorg
``` to make a config and then do ```
startx
``` to start X

---

### Post by madmatrixz3000 on 2008-02-28
I will try that, I have to wait as my XP setup is running right now so that I can setup my sata card so that I can run off my 320Gb drive.

---

### Post by madmatrixz3000 on 2008-02-28
Ok so I just needed to reinstall Studio, because when you select your software, they had the bright idea to have gnome as completely optional even though the programs require a front end, and only can run in Gnome, but Xorg and Gnome are completely optional.

---

