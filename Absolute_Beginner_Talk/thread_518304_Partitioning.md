---
title: "Partitioning"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by henrywm on 2007-08-05
My brother-in-law set up partitions on my laptop when I was trying Fedora. I am now trying Ubuntu. He set up partitions for root, boot, swap, and home. I do not remember which were primary and which were logical. What is the difference?

---

### Post by alienexplorers on 2007-08-05
Just the type of partition.  They all work very simular to one another, so if it is running I would not worry about it.

---

### Post by annda on 2007-08-05
some background info on wikipedia:
[http://en.wikipedia.org/wiki/Disk_partitioning#Primary_.28or_Logical.29](http://en.wikipedia.org/wiki/Disk_partitioning#Primary_.28or_Logical.29)

you need at least 1 primary, and you can have up to 4 partitions on a disk - primary and extended. if you need more, an extended partition can host many logical drives/partitions.

---

### Post by henrywm on 2007-08-05
What is the difference between primary and logical partitions?

---

### Post by alienexplorers on 2007-08-05
A primary partition is a partition made directly to the disk.  A logical partition is made within an extended partition.  An extended partition is made on the drive directly and is made to hold logical partitions.

---

