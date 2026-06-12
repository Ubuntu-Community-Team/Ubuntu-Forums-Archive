---
title: "Help with Intel GMA 950"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by vasudevank on 2006-10-25
I installed ubuntu with no problems. However I don't have a tutorial on which video card driver i need to install

I installed beryl and it crashed because vesa doesn't have 3d support, so I was wondering if anyone had step by step instructions on my xorg.conf file and install things, where im supposed to get drivers and what not, i am really lost.

---

### Post by Qrk on 2006-10-25
That probably isn't the issue. Intel GMA 950 have open source drivers that are included by default, they support 3D acceleration. If you post the error message you got, we could tell you more. Are you sure you installed Xgl before beryl?

---

### Post by vasudevank on 2006-10-26
I am almost positive it crashed because of vesa drivers, I forgot I had to install intel gma drivers, but the beryl wiki was for the gma 855, so I started to use it, then however in synaptics package manager I found xserver-xorg-driver-i810, so i edit xorg.conf to have driver "i810" but I get this:

(WW) I810: No matching device section for instance
(EE) I810(0): No Video BIOS modes chosen depth
(EE) Screen(s) found but none have usable configuration

I set my depth at 1440x900, which is what i run in windows, so I am really lost, if anyone could point me to a tutorial on how to install gma 950 that would be great. Also I downloaded a driver, and it has a .sh, how do i get that to become a driver? (I found a i915 driver, which worked in gentoo linux for many) Thanks for all of your help

---

### Post by vasudevank on 2006-10-26
Any help would be really great. I am really stuck and I really want xgl, so any help would be greatly appreiciated.

---

### Post by zman58 on 2006-11-26
You need to run the 915resolution program. This is part of the 915resolution debian package that you can install on your system. You may already have it installed. Just try viewing the man page for it.

man 915resolution

You can read more about this in another post I made which details the Intel GMA 950 on a DELL D620. Find it here:
[http://www.ubuntuforums.org/showthread.php?p=1808047#post1808047](http://www.ubuntuforums.org/showthread.php?p=1808047#post1808047)

Good luck to you :)

---

