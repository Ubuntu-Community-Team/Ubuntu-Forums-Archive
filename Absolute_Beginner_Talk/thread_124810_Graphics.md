---
title: "Graphics"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by m0o0oeh on 2006-02-02
Well, I bought myself a new graphics card over Christmas, and I installed it on Windows with no problems whatsoever. Now, the graphics on Linux are knackered. Any ideas what's wrong?

J

---

### Post by DiscoKiller on 2006-02-02
what is your new card?

---

### Post by m0o0oeh on 2006-02-28
Soz bout delay - its a GeForce FX5500

---

### Post by taurus on 2006-02-28
It's a nVidia card so what's wrong with it!  Two of my systems are using eVGA GeForce FX5600 video cards and they work real well in Linux.  Make sure you install nVidia driver for it...  

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by Perfect Storm on 2006-02-28
You properly need to reconfigure the xorg.conf files plus if you didn't have a gf card previously you need to install the right files.

---

### Post by Gustav on 2006-02-28
reconfigure xorg.conf by typing this in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
and install the nvidia drivers (preferebly via method 1 in the guide taurus posted)

---

