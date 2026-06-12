---
title: "Booting Problem in Mac"
date: 2012-10-30
forum: Apple Hardware Users
---

### Post by Ibrahim mufeed on 2012-10-30
Hi,

I have Mac machine and I already installed Windows XP on the machine so it was dual boot and things were OK. Today I wanted to install Ubuntu on the machine so I booted from the USB flash and installed Ubuntu. At this time I have the following HD partitions:
1- 200GB for Mac OS X.
2- 300GB for Window XP.
3- 5GB for Swap.
4- 495GB for Ubuntu.

When I boot the machine it used to show the normal Ubuntu boot menu with all the operating systems, but only Ubuntu works! The other two operating systems give error and refuse to boot.

I booted the machine holding the ALT key and it booted normally into Mac OS X. I found out that After making the last two new partitions for Ubuntu the Mac is asking to format all the disk into one single partition. And now when I boot normally (without holding the ALT key) it takes me into OS X, and when I boot holding the ALT key as I want to select other operating system it shows only the Mac OS X partition and it does not show the other operating systems to boot from.

When I go to boot Camp, it says:"The startup disk cannot be partitioned or restored to a single partition.".

I need to fix this problem! I need all of the 3 operating systems.

Any idea?!

---

### Post by risidoro on 2012-10-30
Try installing refit into osx. then poweroff completely and restart. Should be able to find all the OSes . Also, in refit boot menu (a nice graphic boot screen) try the option fix MBR (or something like that, I forgot the original wording). Let us know. Bye and good luck

---

### Post by elctro on 2012-10-31
> **risidoro said:**
> Try installing refit into osx. then poweroff completely and restart. Should be able to find all the OSes . Also, in refit boot menu (a nice graphic boot screen) try the option fix MBR (or something like that, I forgot the original wording). Let us know. Bye and good luck

Yah, in Mac devices rEfIt should be installed first.

---

### Post by Ibrahim mufeed on 2012-10-31
Thanks for your replies. I have installed rEfIt and now I can boot in Mac OS X and in Ubuntu but I can not boot in Windows! It says no bootable device found!

Any suggestions?

---

### Post by risidoro on 2012-10-31
Try MBR fix (or GPT sync) in refit boot menu... I have no more clues...good luck

---

### Post by Ibrahim mufeed on 2012-11-01
> **risidoro said:**
> Try MBR fix (or GPT sync) in refit boot menu... I have no more clues...good luck

Would you tell me with more details what you meant by that? I do not know what I have to do.

---

### Post by rcsheets on 2012-11-01
I just discovered that there's a newer fork of rEFIt, which I'm using with some success. It's called [rEFInd](http://sourceforge.net/projects/refind/). I would recommend it since it seems to be a bit more configurable than rEFIt, and is being more actively maintained.

---

