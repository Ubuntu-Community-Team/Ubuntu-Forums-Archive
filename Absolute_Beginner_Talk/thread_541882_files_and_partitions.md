---
title: "files and partitions"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Marktwo on 2007-09-03
Would someone please tell me how to determine or where I can find out which directories are on which partitions. In particular I need to know which partition has /home on it.  Also what is the extended partition formatted.   Thanks

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19080   153260068+  83  Linux
/dev/sdb2           19081       19457     3028252+   5  Extended
/dev/sdb5           19081       19457     3028221   82  Linux swap / Solaris

---

### Post by taurus on 2007-09-03
Your /home is under /dev/sdb1.  You only have one root partition so everything is under /.

Basically, you can only have 4 primaries partitions and if you need more than 4, you need to convert one of the primaries into extended and then create more partitions, logical, under that extended partition.  Therefore, you swap partition is a logical partition, /dev/sdb5.

---

### Post by lost4now on 2007-09-03
Interesting....  Why wasn't the main partition made to use all of the available disk space. What is the value of the extended partition.

---

### Post by vanadium on 2007-09-03
What you showed was the output of the fdisk -l command. This lists all drives and partitions on these drives, whether mounted or not. Indeed, an experienced user can usually infer from that listing where the root will be mounted. However, to actually see if a partition is mounted and where, run the "mount" command (as such, no "sudo" needed). The first entry is the partition, the second the mount point (/ for the root directory).

---

### Post by laidback on 2007-09-03
For a GUI view of drives try Gparted, System>Administration>Gnome Partition Editor, in 7.04.
If you cannot find it install from Synaptic.
Gives other information as well.

---

### Post by ashishgoel on 2007-09-03
Gparted is good....

---

