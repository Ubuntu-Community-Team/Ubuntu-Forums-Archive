---
title: "Suspect my disk is on its way out"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-10-07
Ive got an 80 GB ide disk i use for my current filesystem /hda

Ive got an additional 80GB SATA drive mounted under sdc which I have formatted as ext3 with 2 gb of swap.
I have copied the entire filesystem from 1 to the other (sata being the destination) and have recreated the uncopyable folders dev and media.

I know how to make sata the boot priority so no problems there, i just need to know how i can make the sata one bootable. Will this work? and if it does will it cause me problems?

I tried to copy the diskimage but the sata one is like one MB smaller so it wont work when using UltimateBootDisk:(

---

### Post by cmnorton on 2007-10-07
You would make the SATA drive bootable using GRUB (or LILO), right? Are you asking this because it's a SATA drive not IDE, or because of the boot order? If you know you can make the SATA drive boot before the ID, you should be able to put a boot loader and kernel in the right place on the drive and do that before powering down.

---

### Post by dgrafix on 2007-10-11
Not exactly, i can control which disk boots under the bios i was simply wondering if i just copied the filesystem from one disk to another (inc hidden files) it would boot off the other drive or not. Ive set the 'flags' to 'boot'

---

