---
title: "Dual Boot"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by bigbrd222 on 2007-11-29
Ok, so I've looked into different places and just can't find out how to set this up how I want to so here goes:

I am running Windows XP Media Center Edition. One HD. 20gigs of space left.

I want to install Ubuntu 7.10 desktop and set it to dual boot.

The thing is, is that my Windows is set up on one large partition, taking up most space on the disk.

How can I make this work, without losing Windows or my data?

---

### Post by bjarneh on 2007-11-29
do you have 20 Gb of "free space" as in not belonging to the Windows partition, or do you have 20 Gb left of your Windows-partition?

---

### Post by bigbrd222 on 2007-11-29
Windows partition.

---

### Post by bjarneh on 2007-11-29
ok, then you need shink your Windows partition a bit before installing Ubuntu, if you have a version of partition magic at hand, this is a very simple matter. gparted-live-cd should offer more or less the same features, although i have never used it:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by bjarneh on 2007-11-29
[http://www.partedmagic.com/](http://www.partedmagic.com/)

or maybe this tool....

---

### Post by bigbrd222 on 2007-11-29
How much?

Does it matter?

How much space does Ubuntu need?

---

### Post by bjarneh on 2007-11-29
once you have shunken your Windows partition, which should be a matter of sliding a ruler to one side until you have maybe 15 Gb or so left of free space, then its only a matter of using that space to install Ubuntu, standard configuration should do (only remember not to use the default option as you install it, which is to use the entire disk i think)

---

### Post by bjarneh on 2007-11-29
how much space it requires depends a bit i guess, not really sure, i have 
8 Gb root directory  /
12Gb for my home directory (where all my personal files are stored)
512 swap or so

currently i'm using about 11 Gb

but i'm not using all of it, if you have a Windows partition with songs or fims and so on, this is not a problem, you can still read these files using Ubuntu, i.e., you can still listen to you Windows music or watch your Windows-films and so on...

---

### Post by bigbrd222 on 2007-11-29
Ok, thank you.

I'll try it and post what happens.

---

### Post by bjarneh on 2007-11-29
yep, there are a few of those "dual-boot" theads here i think, once you get some free space on that hard-drive.

/ - root
 swap is all you need, so

512 Mb of swap, and 12 Gb for / (root) should do it, once you get the space freed up that is

have fun, remember to take a backup if there is something important on that disk

---

