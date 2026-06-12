---
title: "xfs wont use all the disk"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by jc508 on 2007-08-24
Hi,
I am trying to set up the 'remainder' of my disk as as xfs partition but it wont let it go above about 139Gb.
Its a 320Gb SATA drive and I am using Fiesty. 

Is there some magic I am not doing ?  Seeing xfs is supposed ot allow huge partitions.

Thanks
JC


Turned out not to have anything to do with xfs. The installer can't handle partitions > 200Gib; it gives "can't have the end before the start" errors.
The solution was to get a live cd version of gparted and partition the drive BEFORE the installer. (see [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php))
At install time choose manual and change the mount points then it works

JC

---

### Post by nonewmsgs on 2007-09-18
what program are you using to partition?

---

### Post by jc508 on 2007-09-21
The partitioner is part of the live Cd install - I don't know what its called
JC

---

