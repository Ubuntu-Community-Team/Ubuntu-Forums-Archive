---
title: "External USB disk missing"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Robert Leithe on 2006-11-21
Hi,

I'm running Ubuntu 6.10, and am fairly new to Linux.

I have three external USB disks.

Maxtor OneTouch II 300 GB
Western Digital My Book 500 GB
An internal 250 GB disk I mounted in a case myself

All three disks where available (read only) at installation time. The largest of the three is primarily used as a backup. All disks where NTFS at installation time.

I used gparted to format the Maxtor disk to ext3 (unmounted it first - that is I right clicked it and chose eject). Upon completion I powered the disk down and back up to have it remounted. I then copied all the data I wanted from my backup disk. No problems.

I then used gparted to format the 250 GB disk to fat32 (as I wanted to share the content with WinXP users). Again I unmounted it first - that is I right clicked it and chose eject.
But this disk has been missing since. I have tried to power it down and back up. I have rebooted my computer.

When I run fdisk -l I get this

*********************** START OF OUTPUT **************************
robert@C-3PO:/$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36484   293054464   83  Linux
*********************** END OF OUTPUT **************************

When I run gparted again I cannot find the disk there either.

How can I "get in touch" with this disk again?

Sincerely

---

### Post by Robert Leithe on 2006-11-22
After I shut down the computer, and the external harddrives, over night. The disk came back.
But when I unmount it, it automatically remounts. Thus I can't seem to reformat it to ext3 (changed my mind obviously :) )

---

