---
title: "Help with Partitions"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ZeroPain on 2007-04-19
I keep getting the grub 18 error when using the guided installation. Because of this I have been trying to partition manually.

I made the following:
500mb /boot
1536mb swap

Then I attempt to partition the rest of disk as "/" but I get an error saying "Can't partition the end before the beginning!" or something of the sort.

Please help ](*,)

---

### Post by Duck2006 on 2007-04-19
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This may help

---

### Post by bloodniece on 2007-04-19
you really don't need a swap that large. root cannot appear after the swap partition.
 Delete all partitions
Create only a /    (root)
and a swap
or use the guided partitioning helper guy

I set my home as a separate drive hdb1
root is hda1 and swap is hda2

---

