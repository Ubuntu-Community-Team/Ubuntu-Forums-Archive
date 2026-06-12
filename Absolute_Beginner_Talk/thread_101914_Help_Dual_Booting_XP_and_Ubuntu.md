---
title: "Help Dual Booting XP and Ubuntu"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by deliriumx on 2005-12-10
Does anyone know the best way to dual boot these 2 operating systems assuming that I have norton ghost, a 160 gig external HD with stuff I want to keep on it(like 40 gigs I want to keep and its not partitioned) I have a 80 gig internal which I want to keep everything on that, and ubuntu install disc. I really dont want to lose any information or mess up my computer. What order do I partition and install things and where do they need to be installed? Do I need a boot loader? I am prety clueless. Thanks guys.

---

### Post by aysiu on 2005-12-10
Just about everything you need to know:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by nubuntux on 2005-12-11
Hi, a better procedure to install ubuntu is... install first your fav. M$Windows OS, partition your primary drive, (i used partition magic, it really supports linux FS). assign 1 partition dedicated for Ubuntu. follow this;

drive C - M$Windows OS
drive D - [NTFS/FAT parition {optional}]
drive E - [NTFS/FAT parition {optional}]
drive ... - [NTFS/FAT parition {optional}]
lastdrive - format to linux filesystem

or let ubuntu installer do the job of installing the OS, and point it to your lastdrive, to use for UBuntu. Then let ubuntu do the BootLoader --> usually GRUB.... follow some steps.....

good luck!

---

