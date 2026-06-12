---
title: "Matrox P650 driver install"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by pizzadude on 2006-07-08
Made the switch today and I've so far been unsuccessful in sorting out the driver for my AGP based Matrox P650. I've searched the forums for similar topics but those require basic knowledge which I do not yet posess.

Could someone perhaps provide a step by step guide for dummies?

---

### Post by nespa on 2006-07-21
Recently Matrox released a closed source driver version 1.4.4 (amd 64bit support at last!)

Best is to look at [http://www.tuxx-home.at/](http://www.tuxx-home.at/) and get the unofficial driver there ( this is the offical matrox driver plus some patches ).
I suggest you use VESA driver, run this installer, switch /etc/X11/xorg.conf from "vesa" to "mtx".  Works for me.
You will need linux-headers on your system in order to run the installer.

Keep fingers crossed that Ubuntu will provide the convenience of packaging this somewhere in the future to make this all work automagically :p

---

