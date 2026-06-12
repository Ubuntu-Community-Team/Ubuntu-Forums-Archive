---
title: "Removed Ubuntu Partiton from Dual Boot, Getting Grub Error 22"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-10-07
I was dual booting between XP and ubuntu, tried to remove Ubuntu by deleting its partition and now when GRUB runs i get a boot error 22. Can anyone tell me how to boot back into XP?

---

### Post by Pumalite on 2007-10-07
Boot from XP CD and>hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by bobbocanfly on 2007-10-07
XP was installed OEM dont have the CD, is there anyway to do it from a Linux Live CD (Ubuntu 7.10, GParted, Slax 5.1.8.1)?

---

### Post by arkara on 2007-10-07
yep this will do the job
try fixmbr then type exit and reboot the machine
if this does not work then try the fixboot
good luck

---

### Post by arkara on 2007-10-07
nope
boot from the live cd
and then search for on the net for sth..
or reinstall ubuntu this will fix youf grub
and have dual boot ubuntu/xp
then borrow a windows xp cd
and do the job.
this is weird not to have a win xp cd.. xin xp=recovery cd if you have one of that..

---

### Post by Pumalite on 2007-10-07
If not, use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You can boot Windows with it and or fix MBR

---

### Post by bobbocanfly on 2007-10-07
Fixed it with the Super Grub Disk, that thing is properly useful! Thanks.

---

### Post by Pumalite on 2007-10-07
You are welcome. Good luck.

---

