---
title: "Unmounting and moving hard drives"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Atanvarno on 2007-04-21
I've read the wiki pages on mounting/unmounting partitions, but I'm a hopeless newbie who is afraid of everything going wrong and I'm not sure how to proceed.

fdisk -l returns:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13054   104856223+   7  HPFS/NTFS
/dev/sda2           13055       13303     2000092+  82  Linux swap / Solaris
/dev/sda3           13304       30401   137339685   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14946   120053713+   7  HPFS/NTFS

My problem is when I installed Ubuntu I accidentally mounted /dev/sdb1 and /dev/sdc1 to /~/Media and /~/Documents respectively, when I wanted them sat in the home folder. Can some kind soul give step-by-step instructions to fix this, or perhaps a helpful link?

---

### Post by vanadium on 2007-04-21
I am not at all a guru (Ubuntu user since easter) but I know for sure that you will need to fix this in the fstab file. The fstab file is the file that defines at startup time where the different mount points are.

* To find out where fstab lives, type: locate fstab

* To edit the file: gksudo gedit /etc/fstab

You will probably readily be able to fix your error: first comes the device, then the mount point. Simply find your erroneous mount points and replace these by the correct mount point. Your post at the end is not very clear: it sounds to me as if you wanted to mount both drives to the same moint point: don't do that: each device needs its own mount point.

---

