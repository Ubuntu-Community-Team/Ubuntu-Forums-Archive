---
title: "Can I access Ubuntu files in Windows?"
date: 2006-06-08
forum: Apple PPC Users
---

### Post by walterius on 2006-06-08
Thanks to this forum, I can access all my Windows files (they are all FAT32) on every drive in Dapper.

But, lo, I would like to be able to do it the other way, too.

Is there any way I can access all My Dapper files in Windows (2000 or ME)?

I can create or delete linux partitions (Breezy and Dapper) in Partition Magic 8, but I would also be able to access the actual files and their contents.

:rolleyes:

Walterius

---

### Post by Phasmagon on 2006-06-08
There is [this driver]("http://www.fs-driver.org/") for windows to enable to read, write ext2(3) file systems. I have never actually used it.

But why do you need that? I think its best to create a fat32 fs and use it to move data between OSes.

---

### Post by walterius on 2006-06-08
:confused: Phasmagon, you lost me. My Windows file systems are already FAT32. My linux file system is, and has to be, ext3.

My question is, how can I access ext3 from Windows? ](*,)

---

### Post by walterius on 2006-06-08
I decided to try the freeware driver you mentioned. I will post back with the results. Many thanks for the info. :KS

---

### Post by aysiu on 2006-06-08
[QUOTE=walterius]:confused: Phasmagon, you lost me. My Windows file systems are already FAT32. My linux file system is, and has to be, ext3.

My question is, how can I access ext3 from Windows? ](*,)[/QUOTE]
Install the driver Phasmagon linked to.

You install the drive in Windows--it allows you to see Ext3.

---

### Post by aysiu on 2006-06-08
Double post.

---

