---
title: "gfxboot help... from a not 100% noob..."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by kraigory on 2007-07-01
Okay, so I followed the thread [here]("http://ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot") exactly, but to no avail. GRUB works fine, only it is still the old fashioned grub. 

Here is my fdisk output:

```
kraigory@elihu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8517    68364607+   7  HPFS/NTFS
/dev/sda3            8518       11306    22402642+   5  Extended
/dev/sda4           11372       11977     4867695   db  CP/M / CTOS / ...
/dev/sda5            8583       11306    21880530   83  Linux
/dev/sda6            8518        8582      522049+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2048 MB, 2048729600 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992     1999749+   6  FAT16

```

someone told me...

> 

```

sudo grub-install /dev/sdxy
```

Where x is a,b,c,etc. y is 1,2,3,etc.

So I did that with sda5 (my linux partition, right? Here is the output:

```
kraigory@elihu:~$ sudo grub-install /dev/sda5
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda

```

Still no gfxboot, at all...

I'm too much of a noob to know exactly what is going on here... could anyone shed some light?

Thanks!

---

