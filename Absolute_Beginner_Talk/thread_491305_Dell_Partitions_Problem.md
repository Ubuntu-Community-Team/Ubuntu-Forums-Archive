---
title: "Dell Partitions Problem"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by jocamiah on 2007-07-03
I consider myself quite knowledgeable but I am having a bit of a problem installing Ubuntu 7.04 on my friends Dell.  The installation process does not allow me to partition the hard drive.  I tried to manually do it using gparted and the installation's manual partitioner.  It shows no option to resize any of the existing partitions or the hard drive.  Dell has 4 partitions on the hard drive with one that has Win XP installed on it.  So how do I resize the hard drive?

---

### Post by Inxsible on 2007-07-03
> **jocamiah said:**
> I consider myself quite knowledgeable but I am having a bit of a problem installing Ubuntu 7.04 on my friends Dell. The installation process does not allow me to partition the hard drive. I tried to manually do it using gparted and the installation's manual partitioner. It shows no option to resize any of the existing partitions or the hard drive. Dell has 4 partitions on the hard drive with one that has Win XP installed on it. So how do I resize the hard drive?
 
Its probably because all 4 partitions are primary partitions and you can have a max of 4 primary partitions. You will have to delete atleast one partition and create an extended partition, then install Ubuntu in that extended partition by further partitioning it as / (root), swap and a separate /home if you want.

---

