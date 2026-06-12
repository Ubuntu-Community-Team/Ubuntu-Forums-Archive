---
title: "Can't resize ntfs partition"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Will Hanley on 2007-10-09
Hi, I've looked around a fair bit but can't seem to find anything to fix this problem.  I have been using ubuntu for a month, installed on a Windows 2000 machine.  I should have placed the partitions differently when I installed it, but I didn't.  Now I have no free space on my sda2 (ubuntu) partition, but a bunch of space on my sda1 (windows) partition.  Gparted doesn't allow me to resize sda1, which is ntfs.  The "move/resize" command remains inactive after I unmount the partition.

My dim understanding of ubuntu is probably clear to you from the inaccurate language I'm using to describe this problem.  I know what my problem is (no hard drive space), but have little idea how to solve it or even to explain it.

Help!

---

### Post by bigken on 2007-10-09
try using gparted live cd

---

### Post by nvteighen on 2007-10-09
Or also you can use Ubuntu Live CD. In Ubuntu's Live CD, go to System --> Administration and you'll find Gparted there.

---

### Post by kellemes on 2007-10-09
> **bigken said:**
> try using gparted live cd

Agree.. It will not automatically mount the NTFS partition like Ubuntu LiveCD does..
This means you can resize the partition without problems.

---

