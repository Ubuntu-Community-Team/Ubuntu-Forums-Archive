---
title: "Partitions"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by big_bad_brad on 2006-08-31
A week or so ago I dual booted my pc with xp and ubuntu.  Not knowing how much I would enjoy ubuntu I only gave my home partition about 20 gigs, and now I want more for my music and pictures.  Can I adjust the partition sizes now?  If I can is it dangerous?

---

### Post by nazgulord on 2006-08-31
You should be able to, by using a live cd (like Knoppix) with a partitioning program such as QtParted on it.

However, even though the repartitioning is non-destructive (at least when using QtParted) (so your files will not be erased), you still risk losing data as something could go wrong.

My advice to you is to backup your data and then try repartitioning.

Here's a thread on backup and restore:

[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+restore](http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+restore)

nazgulord.

---

### Post by big_bad_brad on 2006-08-31
Thank you.  Another question...I have another drive in my computer, and I would like to format it to share files between os.  I'm assuming it should be FAT32, but don't know the best way to accomplish this.  Should I do it through XP or ubuntu(if you can)?  Does it matter?

---

### Post by richbarna on 2006-08-31
> **big_bad_brad said:**
> Thank you.  Another question...I have another drive in my computer, and I would like to format it to share files between os.  I'm assuming it should be FAT32, but don't know the best way to accomplish this.  Should I do it through XP or ubuntu(if you can)?  Does it matter?

Fat32 is a good choice for both, and yes Gparted (in the Ubuntu repos) will handle fat32 partitioning.

---

