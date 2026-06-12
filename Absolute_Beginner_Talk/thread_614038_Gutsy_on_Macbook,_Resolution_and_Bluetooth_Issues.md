---
title: "Gutsy on Macbook, Resolution and Bluetooth Issues"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Maddux on 2007-11-15
This is definitely the place for me, since I am most certainly an ABSOLUTE BEGINNER as far as Linux is concerned.  I have little experience with command line, but I'm willing to learn.

Anyway, I installed Gutsy Gibbon on my Macbook (1st Generation) using Boot Camp and I've got two issues I'm not sure how to solve:
1) Resolution: The native screen resolution is 1280x800, but that's not selectable as an option.  I'm not sure if it's a driver issue or what.

2)Bluetooth: I have a bluetooth mouse that I use but I'm not sure what to do to pair it with Gutsy.  Some guidance would be hugely appreciated!

Thanks for any help!

---

### Post by Nano Geek on 2007-11-15
> **Maddux said:**
> This is definitely the place for me, since I am most certainly an ABSOLUTE BEGINNER as far as Linux is concerned.  I have little experience with command line, but I'm willing to learn.

Anyway, I installed Gutsy Gibbon on my Macbook (1st Generation) using Boot Camp and I've got two issues I'm not sure how to solve:
1) Resolution: The native screen resolution is 1280x800, but that's not selectable as an option.  I'm not sure if it's a driver issue or what.

2)Bluetooth: I have a bluetooth mouse that I use but I'm not sure what to do to pair it with Gutsy.  Some guidance would be hugely appreciated!

Thanks for any help!I don't know about the Bluetooth problem, but to fix the resolution just run this:```
sudo dpkg-reconfigure -phigh xserver-xorg
```It will ask you a few questions and you will be able to choose your resolution.

---

### Post by Maddux on 2007-11-16
okay, weird thing.  Using the x server configuration I am able to set the x server driver to i810, but for some reason, when I set the supported resolution, it never saves it.  After exiting, if I immediately load the x server configuration again all the selections I just made have been reset.

---

### Post by Nano Geek on 2007-11-16
Could you post what your xorg.conf file looks like before and after a reboot?
Thanks

---

