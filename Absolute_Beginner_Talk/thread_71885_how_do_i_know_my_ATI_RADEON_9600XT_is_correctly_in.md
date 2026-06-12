---
title: "how do i know my ATI RADEON 9600XT is correctly installed, (getting window tracers)"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by thespinesplitter on 2005-10-04
how do i know my ATI RADEON 9600XT is correctly installed it should be but i still get sluggish graphics when i move windows, you guys know the famous tracer effect, im i wrong or my ATI should be redrawing the windows way faster or is it just GNOME

plz im preety noobish and im going crazy, if someone can give me some commands used to monitor devices and to define wich devices are which, that would be more than helpfull

---

### Post by kuku on 2005-10-04
I just installed the Catalyst drivers from the ATI site a few hours ago.  There is a noticable difference in performance between those and just running right after an install.

---

### Post by mlomker on 2005-10-04
>  im i wrong or my ATI should be redrawing the windows way faster or is it just GNOME

The commands are **fglrxinfo** and **glxgears**.  I have a [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911") on installing the drivers.

---

### Post by thespinesplitter on 2005-10-04
well i think i see a difference but im certainly not using the ubuntu generic dirivers im using the apt-get ATI ones, well u could have at-the-least told me if u still get traces when moving windows for conparison purposses

---

### Post by thespinesplitter on 2005-10-04
well.... fglrxinfo reported this, which im kinda concerned about 

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
```

with gears i got 250FPS, this isnt right im seeing benchmarks with 9500FPS with radeon 9600

---

### Post by mlomker on 2005-10-04
> 9500FPS with radeon 9600

From whom?  I average 2500fps out of my mobile 9700.

---

### Post by thespinesplitter on 2005-10-04
right here on ubuntu, search glgears benchmarks

---

### Post by thespinesplitter on 2005-10-04
.

---

### Post by thespinesplitter on 2005-10-04
oh good i rendered my ubuntu unusable by unistalling all the xorg its about to boot me off, it took all the gnome and gnome software with it WOW

---

