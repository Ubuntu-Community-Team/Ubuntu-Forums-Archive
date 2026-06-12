---
title: "Can't find NTFS partition"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by sebastian.goh on 2007-05-26
Hi,

In Windows, I had partitioned my hard disk as C: = system and d: = data.
I had tested out Ubuntu LiveCD and decided to installed Ubuntu Feisty Fawn today erasing Windows. But now I could see my D: drive.

sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7269    58388211   83  Linux
/dev/hda2           13975       14593     4972117+   5  Extended
/dev/hda3   *        7270       13974    53857912+  83  Linux
/dev/hda5           14267       14593     2626596   82  Linux swap / Solaris
/dev/hda6           13975       14266     2345427   82  Linux swap / Solaris

How do see my data drive?

Thanks

---

### Post by drowner on 2007-05-26
> **sebastian.goh said:**
> Hi,

In Windows, I had partitioned my hard disk as C: = system and d: = data.
I had tested out Ubuntu LiveCD and decided to installed Ubuntu Feisty Fawn today erasing Windows. But now I could see my D: drive.

sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7269    58388211   83  Linux
/dev/hda2           13975       14593     4972117+   5  Extended
/dev/hda3   *        7270       13974    53857912+  83  Linux
/dev/hda5           14267       14593     2626596   82  Linux swap / Solaris
/dev/hda6           13975       14266     2345427   82  Linux swap / Solaris

How do see my data drive?

Thanks

It's been deleted.

The install uses the whole DISK, not the whole PARTITION.

---

### Post by Outrunner on 2007-05-26
Umm... I don't see any NTFS or FAT partitions of any kind(did I miss them?). Did you use "Erase entire hard disk ..." to install Ubuntu, when partitioning?

---

### Post by Ek0nomik on 2007-05-26
The install doesn't necessarily use the whole disk, you can have it just use the whole partition.  It depends on how you set it up.  ;)

sebastian.goh:

It looks like you have a weird partition table setup.  Was it your intent to knock out Windows?  If you only want Ubuntu installed, your fdisk -l output should only be Linux and Linux Swap / Solaris.  (Assuming no USB devices being hooked up).

---

