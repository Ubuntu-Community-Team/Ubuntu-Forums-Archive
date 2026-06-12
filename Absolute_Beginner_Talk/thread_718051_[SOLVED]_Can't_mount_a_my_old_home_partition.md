---
title: "[SOLVED] Can't mount a my old /home partition"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-03-07
I have a partition that was dedicated to /home, but I removed the system and I want to mount that partition now. However, it's not showing up anywhere, so I'm guessing I need to remount it. How would I go about doing this?


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b00fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2762    22185733+  83  Linux
/dev/sda2            2763       38913   290382907+   5  Extended
/dev/sda5            2764        2948     1486012+  82  Linux swap / Solaris
/dev/sda6            5499       38913   268405956   83  Linux
/dev/sda7            2949        5498    20482843+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2         637     5108670    5  Extended
/dev/sdb2             638       30401   239079330    b  W95 FAT32
/dev/sdb5               2         637     5108638+   6  FAT16

---

### Post by taurus on 2008-03-07
Which one is your old /home, /dev/sda6 or /dev/sda7?

---

### Post by 449 on 2008-03-07
> **taurus said:**
> Which one is your old /home, /dev/sda6 or /dev/sda7?

sda6

sda7 is my Ubuntu install that I am running off of right now.

---

### Post by taurus on 2008-03-07
```
sudo mkdir /media/old_home
sudo mount -t ext3 /dev/sda6 /media/old_home
ls -la /media/old_home
```

---

### Post by 449 on 2008-03-07
> **taurus said:**
> ```
sudo mkdir /media/old_home
sudo mount -t ext3 /dev/sda6 /media/old_home
ls -la /media/old_home
```

Exactly what I needed. 

Thanks! :popcorn:

---

