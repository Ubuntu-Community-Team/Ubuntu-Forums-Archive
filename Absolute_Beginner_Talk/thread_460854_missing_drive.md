---
title: "missing drive"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by natakim on 2007-06-01
i just formatted one of my hard drives to ext3 using gparted, now when i go to places/computer to drive doesn't show.

> Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      484521   244198552+  83  Linux


i get this in terminal from sudo fdisk -l

what happened to my drive? 

cheers

edit. sorry forgot to mention i'm using ubuntu 7.04

---

### Post by sandwitch on 2007-06-01
is it mounted? mount | grep sdb should give a short answer to that

---

### Post by natakim on 2007-06-02
> **sandwitch said:**
> is it mounted? mount | grep sdb should give a short answer to that

i've since rebooted, now the drive is up visible again in system. i'm really confused by the lack of read/write permissions on two of the drives. have used NTFS configuration tool, but it only seems to grant access to windows drive, and not the external, which is also ntfs. also, why is the ext3 inaccessible?

---

