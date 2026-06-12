---
title: "Partitioning Help"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by jrs0390 on 2007-07-17
Im  a new user and am currently dual booting Ubuntu 7.04, and Windows XP, and have 4 primary partitions, an NTFS for Windows XP, ext3 for Linux, an "extended" one for my swap file, and a fat32 which i believe has something to do with my startup. I was wondering how i might be able to repartition my NTFS to add a Fat32 partition for sharing files between Windows and Linux. Any help would be greatly appreciated. Thank you.

---

### Post by wolfen69 on 2007-07-17
make things simple and put each OS on its own drive.

---

### Post by bretticus on 2007-07-17
Or if you wanna get around the FAT32 4GB filesize limit (dvds, etc.) just install [Ext2 IFS]("http://www.fs-driver.org/index.html"). I believe it's the same thing I'm using right now. You can mount your linux ext2/3 partions in windows. Works pretty good so far.

---

