---
title: "External HD switched to Read only."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by iain006 on 2007-06-25
Hi,

I've recently encountered a problem with my external hard-drive.  I recently got it back from the shop and there were no problems.  However, a few days ago I accessed it again and found that it had switched to "root" and read only.  I used "gksudo nautilus to try to switch it to my user account but it wouldn't allow it.  An error message appears stating "Owner cannot be changed.  "New Volume" is read only.  

Anyone know how I can resolve this?

Thanks in advance.

---

### Post by ikonia on 2007-06-25
what file system is on this disk ?

if it is fat then the only options you can set are the mount permissions as fat doesn't support permissions.

try re-mounting it with read-write mount options -o rw

---

### Post by iain006 on 2007-06-25
I ran "$ sudo fdisk -l" and got the following details.

+++++++++++++++++++++++++++++++

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7002    56243533+  83  Linux
/dev/sda2            7003        7301     2401717+   5  Extended
/dev/sda5            7003        7301     2401686   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    7  HPFS/NTFS

+++++++++++++++++++++++++++++++++++

So it's in NTFS.

---

### Post by ikonia on 2007-06-25
there you go then,

NTFS is read only unless you use the NTFS-3G/Fuse support packages.

---

