---
title: "ext3fs vs ext2fs"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-19
What are the benefits of ext3 disk format as opposed to ext2? Also, is it possible (and/or advisable) to convert an ext2 partition to ext3?

---

### Post by pay on 2006-12-19
If you convert your partition to ext3 then you will lose the data. Look at this [http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/di8k-debian/node29.html](http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/di8k-debian/node29.html)

---

### Post by John E on 2006-12-19
Thanks - I couldn't see anything in that article about losing all the data but in any case, there doesn't seem to be a great advantage in converting my partitions to ext3.

---

### Post by meng on 2006-12-19
I don't know about there being no great advantage - e.g. when I run Linux from a pendrive (formatted to ext2, because I want to minimize write cycles and prolong the life of the drive) and it crashes (usually because I've inadvertently switched the drive to write-protect, which you definitely don't want to do), I have to fsck it and that's a real pain. Granted, you may not crash as often with your system, but it's good to know that if you do, you can recover more quickly and reliably.

---

### Post by hod139 on 2006-12-19
> **pay said:**
> If you convert your partition to ext3 then you will lose the data. Look at this [http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/di8k-debian/node29.html](http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/di8k-debian/node29.html)


This is just wrong, you will not lose your data and it is very easy to convert.  All you need is tune2fs.  The benefit of the ext3 is the journal.  See [this site]("http://www.troubleshooters.com/linux/ext2toext3.htm") for how to convert.  The steps are basically:
 ```
tune2fs -j DRIVE 
```Where DRIVE is /dev/hda1 for example.  
Note that once you have done that **you then need to edit** 
 ```
/etc/fstab 
```and change  
 ```
ext2
```to  
 ```
ext3
```for the partition's filesystem.

---

