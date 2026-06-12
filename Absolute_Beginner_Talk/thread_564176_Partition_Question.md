---
title: "Partition Question"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-09-30
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.

It is not possible to create more than 4 primary partitions?

---

### Post by Pumalite on 2007-09-30
No

---

### Post by Nessa on 2007-09-30
Bummer

---

### Post by eph1973 on 2007-09-30
You can only have 4 primary partitions.  After that, they need to be logical partitions (basically a virtual partition withing the primary partition).

---

### Post by mikewhatever on 2007-09-30
> **Nessa said:**
> ...
It is not possible to create more than 4 primary partitions?

No. If you already have 4 primary partitions, and what more, you must delete one of them, create and extended one in the unallocated space and then create the required number of logical partitions. That's the deal, bump it or not.

---

### Post by Nessa on 2007-09-30
what's logical?

---

### Post by Pumalite on 2007-09-30
What comes after primary.

---

### Post by Nessa on 2007-09-30
secondary? tertiary?

---

### Post by eph1973 on 2007-09-30
It's the name that the computer industry chose for a virtual partition within an extended partition, which is, essentially, a primary partition, but one that allows you to have logical partitions :-P
Here is a [link]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html") that may provide better explanation.  Anyway, like mikewhatever said, if you already have 4 primary partitions, in order to make more partitions, you need to delete one of the 4 primary, then make an extended partition.  The extended partition is basically a "container" for logical partitions, if you will.  Normally, in Linux, this is unnecessary, and I really haven't seen anyone do this sort of thing for quite some years (back when you needed the smaller partitions because of the way the MS-DOS FAT16 worked).

---

### Post by Nessa on 2007-09-30
I want to install Gutsy and other Linux distros. Thanks for the info! :)

---

### Post by Pumalite on 2007-09-30
Good luck. Happy Ubuntuing!

---

### Post by Nessa on 2007-10-05
How do you create a logical partition?

---

### Post by Pumalite on 2007-10-05
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

