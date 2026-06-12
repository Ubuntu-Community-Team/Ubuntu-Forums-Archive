---
title: "Removing GRUB"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by dancullen on 2005-11-14
hey guys, i need some help with this, im not sure what to do.  I'm pretty much a n00b to linux but not too bad, and my problem is:

-  My PC has 2 hard drives in, the first on Win ME (lol), and then i added the second and installed Ubuntu.  Now when i boot, GRUB comes up and asks me which one i want to boot.  But, if i take either one out, the computer will not boot.  I now want to use these drives in seperate computers, is there any way of removing grub and keeping my installs and data intact, or is reformatting the only way.

Thanks a lot, Dan Cullen

---

### Post by Kyral on 2005-11-14
GRUB is on the Master Boot Record(MBR) of whatever drive the BIOS boots to first (Usually the IDE Master). The best way to find this out is by jumping into your BIOS (procedure varies per Motherboard/BIOS, usually something like "Hit DEL to enter Setup") and looking at the boot order entry.

Though you could always delete GRUB by booting into Me Recovery from the CD and using fixmbr, though this will also make Ubuntu inaccessable until you reload GRUB with the Install CD Rescue mode

---

