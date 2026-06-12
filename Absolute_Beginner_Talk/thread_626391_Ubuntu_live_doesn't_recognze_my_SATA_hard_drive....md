---
title: "Ubuntu live doesn't recognze my SATA hard drive..."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Tallegio on 2007-11-29
I have a new Seagate 250GB SATA hard drive. I have not done anything to it, so it is probably in RAW format. Ubuntu live won't recognize it though. Is there anything I might be doing wrong? Can Ubuntu even work with RAW?

BTW, I'm currently partitioning my WD passport (external drive) which it did recognize for some reason. Will this work until I can figure out the SATA?

---

### Post by kellemes on 2007-11-29
Does "fdisk -l" show the disk?
Try to run GParted to format the disk.

---

### Post by Tallegio on 2007-11-29
Sorry to be a noob, but I don't know how to do either of those things. Do I urn fdisk in the BIOS or somewhere in Linux. 

And I assume gparted will show up under applications in linux?

---

### Post by martinsmayhem on 2008-05-08
hello. i am relatively new to ubuntu but know the rough basics. i have a 500gb seagate. and im having the same problems. i have tried sudo fdisk, and the partition editor. neither will recognise my hdd. it doesnt evan show up. i have been told it may need to be enabled in some way. as of yet i have had no sucses. but im determined to get it installed one way or another.......

---

