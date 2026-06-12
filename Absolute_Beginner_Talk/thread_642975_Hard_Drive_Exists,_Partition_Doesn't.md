---
title: "Hard Drive Exists, Partition Doesn't"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-12-17
On one of my hard drives, GParted shows:

(unformatted) 10GB
/dev/sda1 (FAT32) 140GB
(unformatted) 10GB

(it's a long story why it's weird like that, but bear with me :D). It clearly shows that it is /dev/sda1; however, under properties, it says that /dev/sda1 doesn't exist. Also, "ls /dev | grep hd" shows hda, but no hda1.

Any idea why it would be able to see the hard drive, accurately get the partition structure (even the file system), but not exist?

---

### Post by jken146 on 2007-12-17
Please post the contents of your /etc/fstab file.

---

### Post by Regel on 2007-12-17
There's a program called 'testdisk' that might be able to restore your partition table (and lost partitions).

---

