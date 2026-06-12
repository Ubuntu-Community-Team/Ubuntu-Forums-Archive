---
title: "Installed Linux, cant load windows (grub issue i think)"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by hxzero on 2008-01-21
I had this problem a few years ago and gave up to reinstall windows because of it. I had windows and linux installed on my first hard drive, then took linux off when windows wouldnt boot. now i have linux on a separate hard drive and i cant figure out any way to boot just to windows. here's my fdisk -lu

/dev/hda2  W95 Ext'd (LBA)
/dev/hda5  HPFS/NTFS
/dev/hdb1  Linux
/dev/hdb2  Extended
/dev/hdb5  Linux swap / Solaris

I can see hda5 in Ubuntu, the only problem is, on windows i have a C and a D drive. i can only see the D drive, and i think thats why i cant boot to windows. I've tried mapping and switching my hard drive partitions to hd0,0 with grub, and tried using supergrub to boot straight into windows to no avail. any suggestions? if i can just boot windows i'll be fine because now i know how to avoid this problem. thanks.

---

### Post by torgrot on 2008-01-21
Can you cut and paste the actual output of fdisk -lu  ?  There seems to be a partition missing from your output.  Where is hda1?

torgrot

---

### Post by hxzero on 2008-01-21
i had ubuntu installed on hda1 before i removed it (linux was on the hard drive before windows was). anyways here it is.

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf18cf18c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2        40965750   156280319    57657285    f  W95 Ext'd (LBA)
/dev/hda5   *    40965813   156280319    57657253+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb57bb57

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    57641219    28820578+  83  Linux
/dev/hdb2        57641220    58637249      498015    5  Extended
/dev/hdb5        57641283    58637249      497983+  82  Linux swap / Solaris

---

### Post by torgrot on 2008-01-22
You won't be able to boot Windows off of hda, since there isn't a primary partition.  I would suggest that you back that drive up and re-install windows into a primary partition.  Windows is very particular about booting off the first hard drive first primary partition.

torgrot

---

### Post by hxzero on 2008-01-23
Ok, well thanks for the help.

---

