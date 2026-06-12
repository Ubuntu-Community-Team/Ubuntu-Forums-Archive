---
title: "a partition that both linux and windows can read from"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by sdbkr on 2007-05-28
Hi i am using gparted to format a second hard drive. can someone tell me what is the best system to use so that the files i put there can be written by linux and read by windows? ext3 ext 2 fat 16 fat32 linux swap or resiserfs ? 
thanks

---

### Post by vtel57 on 2007-05-28
FAT32 will work very well for this purpose. My common storage partitions are FAT32 on my system to allow access from any OS.

Luck!

---

### Post by aysiu on 2007-05-28
At this point, FAT32, Ext3, or NTFS could all work. If you are worried at all about problems, your safest bet is FAT32, but keep in mind that you can't have files larger than 4 GB on FAT32 (no DVD backups).

---

### Post by allix on 2007-05-28
I would recommend using ext3 and then installing the file-system driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) in windows.

---

### Post by sdbkr on 2007-05-28
thanks for the suggestions. i used fat32 which for some reason also changed the permissions on the drive so i can now access it. before i couldn't write to it.

---

