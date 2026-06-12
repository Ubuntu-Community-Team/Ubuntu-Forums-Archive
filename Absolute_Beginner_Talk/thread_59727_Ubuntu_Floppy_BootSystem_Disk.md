---
title: "Ubuntu Floppy Boot/System Disk"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by Opteron on 2005-08-25
Hi,
The computer that i install ubuntu 5.04 does not support booting from CD-ROM. So I have to have a boot disk which i could not find. 

In fedora/red hat you simply write the boot.img with rawwritewin.exe and make the floppy. Open with it and insert CD that's all.

In old win9X you put windows system disk and open with cd-rom support. Insert CD and chenge to cd drive and that's all.

How can I do this with ubuntu?

---

### Post by heimo on 2005-08-25
These instructions should be helpful:
[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

If you encounter any problems, don't hesitate to ask. :)

---

### Post by Opteron on 2005-08-25
Thanks for the quick reply.

It says that:
Warning SBM is not compatible with parted if installed on harddisk MBR. Parted may detect wrong partition information! 

I have 3.2 GB ATA one-partition HDD. Does it cause a problem with installation? or any pre-caution should I take?

---

### Post by heimo on 2005-08-25
Sorry to say, I don't have any idea on this one. If you don't have anything else on that computer and SBM lets you continue, go ahead and try, very unlikely that it could do anything unrepairable. I'd just try. Be sure that you follow instructions on that wiki-page (linked above).

parted refers to program that is used to partition / resize partitions during install

---

### Post by GeirG on 2005-08-25
I don't have much experience with SBM, but I am pretty sure the warning is ony regarding installation ov SBM on the HD as a boot manager (that is, after all, just what the warning implies).
As long as you just use it as a boot-floppy, SBM doesn't really touch your HD.

So, make the floppy, use it to boot the PC , and choose "CDROM" form the boot menu.
After that, I don't see that SBM is involved anymore.
I guess there is some small chance that SBM does not recognice your CD-ROM, but that would be a different problem.

Good luck,

---

