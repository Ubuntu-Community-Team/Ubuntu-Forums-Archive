---
title: "Problems With GParted"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by TriJump on 2006-08-19
I partitioned my harddrive, but once the partitioning was completed there are now triangular warning signs with exclamation marks in them next to each of the partitions that I created and for filesystem, they all say unknown.  Any idea what has happened?

---

### Post by Adrenal on 2006-08-19
No worries brother, you just havn't formatted it yet. set to ext3 and you should be fine

---

### Post by kopo88 on 2006-08-19
Are you installing Ubuntu from scratch, or are you trying a dual-boot with Windows?

If you're installing from scratch (or erasing and overwriting Windows), then yes, you need to format the partitions.

However, if you had a Windows installation that you wanted to **keep**, and you resized your NTFS partition to make room for Linux, and now you're getting these errors, that means that your partition table was corrupted. If this is the case, do **NOT** format anything. You'll need to repair your partition table. The best tool for this is TestDisk ([http://www.cgsecurity.org)](http://www.cgsecurity.org)), which can be found on the Ultimate Boot CD ([http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)) and some Linux Live CDs.

---

### Post by djsroknrol on 2006-08-19
If it is NTFS then kopo88 is right...however if it's formated fat then adrenal is correct...

---

