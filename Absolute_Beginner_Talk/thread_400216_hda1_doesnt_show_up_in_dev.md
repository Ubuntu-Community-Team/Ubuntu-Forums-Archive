---
title: "hda1 doesnt show up in /dev"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-04-03
Hi I am trying to access my windows harddrive but looking in the /dev folder there is nothing that starts with hda or hd.  Please suggest what I could do to fix this.

Best regards,
outer_space

---

### Post by Maestro23 on 2007-04-03
Post output of:

> sudo fdisk -l

---

### Post by outer_space on 2007-04-03
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5287    42467796    7  HPFS/NTFS
/dev/sda2            5288        9544    34194352+  83  Linux
/dev/sda3            9545        9729     1486012+   5  Extended
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris


I see.

---

### Post by compmodder26 on 2007-04-03
You want to look at /dev/sda1

---

### Post by taurus on 2007-04-03
> **outer_space said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5287    42467796    7  HPFS/NTFS
/dev/sda2            5288        9544    34194352+  83  Linux
/dev/sda3            9545        9729     1486012+   5  Extended
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris

I see.

Yip.  It's /dev/sda, not /dev/hda.

---

### Post by Maestro23 on 2007-04-03
I concur:

> /dev/sda1

---

