---
title: "Does Windows recognize partitions created with gparted?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-12-03
Does Windows recognize partitions created with gparted? :confused:

If not........ can gparted create more partitions from another partition formatted as NTFS using Windows?

agerfe

---

### Post by 449 on 2007-12-03
If the partition was formatted to NTFS in Gparted I don't see why it wouldn't be recognized by Windoze.

---

### Post by Jose Catre-Vandis on 2007-12-03
[COLOR="Gray"]Does Windows recognize partitions created with gparted?[/COLOR]

Yes, but you may have problems seeing and accessing it if an ext2/3 reiser etc partition.

[COLOR="Gray"]can gparted create more partitions from another partition formatted as NTFS using Windows?[/COLOR]

Not sure what you mean by this? You would have to shrink partitioned space to create more partitions??

---

### Post by Het Irv on 2007-12-03
I have heard of people having problems partitioning drives with something other than Vista if it is installed.  If you have Vista the best thing to do is to use the Vista Partitioner.  Otherwise you should not have any problems.

---

### Post by lvleph on 2007-12-03
The one problem with using gparted is that windows doesn't like to be moved.  I deleted a partition yesterday and moved the windows partition to the front of the drive, now I have problems. If you are just resizing a partition and then creating a partition from the free space you will most likely be fine. I did the latter on one of my computers and it worked just fine. The prior I did on another and I have problems.

---

### Post by adhuvi on 2007-12-14
How do i lunch vista partitioner? I'm trying to install kubuntu on an HP Laptop but i can't resize pertition whith the kubuntu installation cd. I also tried with gparted but it just can't resize partition, an error occurs.

---

