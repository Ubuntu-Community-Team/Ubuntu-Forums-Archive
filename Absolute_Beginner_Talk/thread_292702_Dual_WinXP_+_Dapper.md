---
title: "Dual WinXP + Dapper"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Frex on 2006-11-04
Yesterday I installed my first Linux, namely Ubuntu 6.06, on my laptop. I've kept my WinXP installation, because I need it for work. Now, all of my files are in the NTFS partition, but I can't reach them from Ubuntu. How do I solve this? Need I make an extra FAT32 partition for my files?

---

### Post by goodfella on 2006-11-04
From what I know and have read Linux only supports read/write access to fat32 partitions.  Write support for NTFS is not fully supported although you can do it, but just make sure you back up your ntfs partition in case there are bugs.

This link shows you how to configure linux to allow access to your windows partitions.  I used it to set up mine.
[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by Kateikyoushi on 2006-11-04
You can read ntfs partitions from ubuntu all you need is to mount them, it is possible to write to NTFS partitions but I would rather recommend to use the ext drivers and write to the ubuntu partition from windows and just read windows partitions.

Mount NTFS partitions in linux.[LINK]("http://ubuntuguide.org/wiki/Dapper#Windows")
Driver to read ad write ext partitions from windows. [LINK]("http://www.fs-driver.org/")

---

