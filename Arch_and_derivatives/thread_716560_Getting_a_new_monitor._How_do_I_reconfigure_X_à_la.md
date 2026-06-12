---
title: "Getting a new monitor. How do I reconfigure X à la ubuntu?"
date: 2008-03-06
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-03-06
I'm going to get a new LCD monitor to replace my crappy 14" CRT for my  pretty old desktop running Arch + XFCE. I'm not going to change the nvidia GPU (legacy TNT type) it already has. 

My question here is how do I reconfigure X should Arch fail to auto detect new resolution and refresh rate? 

Is there anything similar to dpkg-reconfigure xserver-xorg à la ubuntu?

---

### Post by fwojciec on 2008-03-06
Just edit the xorg.conf.  Or have a look in the wiki (Beginner's Guide is likely kept most up to date) and generate a new config file.  Still, the current version of xorg-server is likely going to be fairly good at autodetecting -- as long as you have all the necessary drivers installed.

---

### Post by deepclutch on 2008-03-06
use xorgconfig to generate a working /etc/X11/xorg.conf in Arch Linux.

---

### Post by jseiser on 2008-03-06
you could also run hwd -xa, it will detect your stuff, and configure xorg as good as it can.  Which will work, you can also use arch's nvidia-xorg tool, check the wiki, their are a few ways to handle waht you need.

---

### Post by deepclutch on 2008-03-06
^ofcourse!thx :p I forgot that!
discover in Debian
kudzu in Fedora
and
hwd in arch :p

---

### Post by canistra on 2008-03-08
no need in manual configuration of xorf.conf, just run nvidia-xconfig as root

---

### Post by MisfitI38 on 2008-03-11
Beware that ```
hwd -xa 
```
will completely overwrite any existing xorg.conf.
```
hwd- x
```
may be a safer option for you. ;)

---

