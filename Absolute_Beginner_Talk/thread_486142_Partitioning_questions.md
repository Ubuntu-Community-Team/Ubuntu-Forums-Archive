---
title: "Partitioning questions"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-27
Ok, i am trying to set up a dual-boot windows xp/ubuntu 7.04

Im not having a problem creating the partitions, but i am, however having a problem with what options to set for each partition.

As it stands now, i have a 30 GB hd partitioned like this

Partition #1: 15.0GB Primary Windows
Partition #4: 8.0 GB ext3 Primary /Home
Partition #2: 6.0 GB ext3 Primary /
Partition #3: 1.0 GB Primary swap

The question i have is what do i do with the other options for each partition such as label, and bootable flag.

---

### Post by bodhi.zazen on 2007-06-27
label is optional, give it what name you want (if any).

You can mount with LABEL=<name> as an alternate to mount /dev/hdax ...

mount LABEL=home /home

or in fstab

Label=home /home ext3 ....

The boot flag is not used by Linux (used by DOS/Winodws) so you can ignore that one as well.

---

### Post by ITdrummer on 2007-06-27
so basically, once i set up the partitions and the appropriate sizes, i am finished?

No more settings need to be changed?

---

### Post by ITdrummer on 2007-06-27
also, what is the difference between ext3 and ext2?

---

### Post by carlosqueso on 2007-06-27
ext3 is a journaling file system which keeps better track of where files are on the disk and so needs to be checked less often.  ext2 is an older filesystem, which doesn't use journalling, and needs to be checked constantly.  You should probably use ext3.  

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) for you filesystem information.

---

### Post by xzero1 on 2007-06-27
I would make the xp partition 'bootable' though probably not needed if grub is used.

---

