---
title: "Partition Trouble"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by falcons7 on 2007-02-05
I seem to be having a problem with one of my partitions. I ran partition magic to try to resize my ntfs partition and add it to my ubuntu ext3 partition. when i rebooted my ubuntu partition stayed the same and the ntfs lost the partition space. I used cfdisk and it says that the new partition is unallocated. I have tried writing the partition but every time i get the same message: Wrote partition table, but re-read table failed.  Reboot to update table.   I've even tried using the partition editor in windows but no luck. Any suggestions?

---

### Post by meng on 2007-02-05
Try downloading and burning the GParted LiveCD and see if that gives you better results. You have nothing to lose, except a CD.

---

### Post by taurus on 2007-02-05
Boot your machine with the LiveCD and use gparted from the CD to merge that empty space to your Ubuntu.  You can't merge it to Ubuntu while you are running Ubuntu.

---

### Post by bodhi.zazen on 2007-02-05
Yes, as taurus indicated you need to resize the partitions from a live CD.

As meng directed the gparted live CD is useful to have around and worth the download and burn ...

But the order of the free space also is important.

I assume you have :

NTFS
Free space
Ubuntu

You need to move the Ubuntu partition so the free space follows the ubuntu root partition.

Like this:

NTFS
Ubuntu
Free Space

Then you can resize the Ubuntu root partition. 

ie free space must follow your partition not be in front of it.

HTH

---

### Post by falcons7 on 2007-02-06
Thanks for the help:) :) :)

---

