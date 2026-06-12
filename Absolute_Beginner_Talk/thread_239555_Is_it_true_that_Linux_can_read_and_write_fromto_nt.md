---
title: "Is it true that Linux can read and write from/to ntfs?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Izuil on 2006-08-19
I read on another forum that Linux can read and write from/to an ntfs partition with the kernel 2.6.XX.

Is this true?

EDIT: BTW what kernel version is dapper drake using?

---

### Post by zxee on 2006-08-19
[http://www.ubuntuforums.org/showthread.php?t=185235&highlight=ntfs+compatibility](http://www.ubuntuforums.org/showthread.php?t=185235&highlight=ntfs+compatibility)

2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

---

### Post by Daremo on 2006-08-19
Linux can comfortably read an NTFS partition, however writing is still highly  unstable can can cause corruption and data loss on the NTFS drive. Writing to NTFS is usually not reccomended.

---

### Post by Contrid on 2006-08-19
I currently dual boot XP and Ubuntu, and have a third FAT32 partition set up to share the data between the two OS's. It was recommended by other members on this forum, and works great. Give it a shot!

---

### Post by jimmygoon on 2006-08-19
Using the new ntfs-3g driver, reading **and writing** NTFS in linux is actually quite stable under normal circumstances.

---

### Post by David Corrales on 2006-08-19
Some will think I'm crazy, but I prefer using an ext3 partition as a shared space. Since ext3 is open, there's already a kernel-level ext3 driver for windows which works great and you get to keep all your file permissions correctly.

---

### Post by givré on 2006-08-20
You are totaly right, it's always better to use ext3 for shared partition, the ext2 driver for windows will always be better than the ntfs for linux, even if it's getting better and better this time, simply because ext2 is open source and ntfs is close source.

Look at the beginning of [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
 if you want to know more about ntfs for linux

---

