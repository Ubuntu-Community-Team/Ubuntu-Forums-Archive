---
title: "No root file system"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by LovesToDance on 2007-12-27
BootIt NG is the boot/partition manager on my PC.  There are three NTFS partitions on one 120 gig HDD in the primary master position.

Windows XP Pro runs on the first partition.  Windows XP home runs on the second partition.  No operating system runs on the third partition, whose capacity is 55 gig.  I would like Ubuntu to run from this partition.

Using Manual Install of Ubuntu 7.10 on the third partition gives this error message: "No root file system is defined.  Please correct this from the partitioning menu."

I can't figure out how to use the partitioning menu to correct this problem.  I need very specific, detailed instruction for using the partitioning menu.

Previous threads in this forum provided no help.

Any suggestions?

Thanks

---

### Post by LaRoza on 2007-12-27
Use GParted to delete the third partition if it is defined as a partition (click on it and delete it) if it is just unallocated space, create two partitions, one large one formatted as EXT3 and one small one (512 MB) formatted as Swap.

GParted is best used as a live cd, see the link in my sig, and is also found on the Ubuntu Live Disk.

Install Ubuntu (/ root) to the EXT3 partition and use Swap as Swap.

---

### Post by LovesToDance on 2007-12-27
Thank you for your prompt response.

How do I access GParted?

---

### Post by AndyCooll on 2007-12-27
You'll need to install it first:

```
sudo apt-get install gparted
```
or via Add/remove.

:cool:

---

