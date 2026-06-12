---
title: "Figuring out what is my Linux partition..."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by unexpected on 2007-10-18
I'm trying to install Gutsy. I currently have feisty installed on one of my hard drives, and would just like to reinstall Gutsy over it.

However on my other drive is my windows xp partition. I'd like to keep that intact. When I launch the installer, it doesn't tell me which is which- it just shows SCSI1 (0,0,0) (sda) for one my drives and SCSI3(0,0,0) (sdb)  for the other other drive.

Is there a way to detect which one has Feisty installed on it?

---

### Post by Hobo Joe on 2007-10-18
The install will show you the size and format of the partitions. Ubuntu partitions are ext3, and Windows partitions are NTFS. That should be enough to tell the difference.

---

### Post by p_quarles on 2007-10-18
Sure. Boot into Feisty, open a terminal, and type
```
sudo fdisk -l
```
The output will give you the systems associated with various disks and partitions. Look for the one that says "Linux," and make a note of whether it starts with sda or sdb.

---

### Post by unexpected on 2007-10-18
> **p_quarles said:**
> Sure. Boot into Feisty, open a terminal, and type
```
sudo fdisk -l
```
The output will give you the systems associated with various disks and partitions. Look for the one that says "Linux," and make a note of whether it starts with sda or sdb.

perfect, thanks!

---

