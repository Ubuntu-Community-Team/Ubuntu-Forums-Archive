---
title: "How do i Create a partition and Format"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by jusmurph on 2007-06-05
```
sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        6256    19535040   83  Linux
/dev/sda3            6257        6499     1951897+  82  Linux swap / Solaris
/dev/sda4            6500       10146    29294527+  83  Linux

```

I want to create sda5 to use up the rest of the drive for storage as a Linux partition, the question is, how do i do that?

Thanks?

---

### Post by earobinson on 2007-06-05
you may want to install gparted and just use that, it has a gui an everything!

---

### Post by HotShotDJ on 2007-06-05
You'll need to remove one of the primary partitions (probably /dev/sda4) and create an extended partition in which you can create multiple logical partitions.  I would download, burn, and boot up from [SystemRescueCD]("http://www.sysresccd.org/Main_Page"), use partimage to backup /dev/sda4, then use gparted to delete sda4, create the extended partition, then create and format two logical partitions.  Now, you can go back to partimage and restore the backed up partition to one of the new logical partitions and use the last one any way you see fit.  REMEMBER!!  You'll need to update /etc/fstab after you do this!

(It sounds WAY more complicated than it really is!  Just be careful, especially with backing up the existing sda4 partition.  You'll probably want to Google and read up on systemrescuecd, partimage, and gparted to be sure your familiar with these programs BEFORE you start.)

---

### Post by vanadium on 2007-06-05
It may not work because you have the maximum of four partitions. As far as I know, you would have to delete one partition and create an extended partition before you can create additional partitions in that extended partition. Thus, be carefull in what you do and do not be surprised if it won work right away.

By the way, the terminal commands for doing this are

sudo fdisk /dev/sda
sudo mkfs -t <type> /dev/sda5 where type is vfat or ext2 or ext3 etc

The fdisk utility is "interactive" with a text based menu. You cannot resize existing partitions preserving their data as with gparted.

---

### Post by earobinson on 2007-06-05
you can also run gparted from the live cd!

---

