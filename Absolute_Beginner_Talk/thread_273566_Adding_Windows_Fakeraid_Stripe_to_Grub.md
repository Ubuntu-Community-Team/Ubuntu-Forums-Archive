---
title: "Adding Windows Fakeraid Stripe to Grub"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by MouseAT on 2006-10-08
I've given up trying to put Ubuntu on fakeraid, and have installed Ubuntu on an old IDE hard disk, set as secondary master. I've got Windows on a fakeraid stripe as well, and I'd like to add Windows to the Grub boot menu. Problem is, I don't know how.

I've installed DMRAID on Ubuntu, although I'm not sure that's necessary.

I understand I'll need to edit the menu.lst to add a Windows entry, but I'm not sure how to point it at the stripe. Here's the ouptut of fdisk -l

```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        3745    30081681   83  Linux
/dev/hdc2           18701       19457     6080602+   5  Extended
/dev/hdc3            3746       18700   120126037+  83  Linux
/dev/hdc5           18701       19457     6080571   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

