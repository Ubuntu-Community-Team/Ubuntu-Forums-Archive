---
title: "Installer doesn't detect my ATA hardrive"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by FredDre on 2007-05-15
I'm trying to install Ubuntu.
I have 2 HDD
One with 250GB with 4 primary partitions (so I cannot add a new one for Ubuntu)
and another one of 80GB.

I'm trying to install it to that drive, but neither the Installer nor GParted detect it.
In GParted it appears as /dev/sdb with 512.00B of unallocated space.

In WindowsXP I can see it, but it doesn't seems to be recognized by Ubuntu.

here is the result of sudo fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3015    24217956    7  HPFS/NTFS
/dev/sda2            3016       21516   148609282+   7  HPFS/NTFS
/dev/sda3           21517       23474    15727635    7  HPFS/NTFS
/dev/sda4           23475       30401    55641127+   7  HPFS/NTFS

Disk /dev/sdb: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

Please, I need help

---

### Post by netwerx on 2007-05-15
What type of filesystem is on the hard drive in question? Is it a basic or dynamic? if you can see it in windows, check in your disk management. if running 2000/xp/vista.

---

### Post by FredDre on 2007-05-15
Logical NTFS. Maybe that is the problem, I should convert it to Primary.

---

### Post by netwerx on 2007-05-15
do you care about the info on this HD?

---

### Post by FredDre on 2007-05-16
Yes, a lot.

---

### Post by FredDre on 2007-05-16
I still need help.

---

