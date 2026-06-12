---
title: "Would this partition table work?"
date: 2009-07-03
forum: Apple Hardware Users
---

### Post by dman777 on 2009-07-03
I am trying to plan a multi boot partition table on a new Macbok Pro 13". I will be using OSX, Windows XP, and Linux. I would like to make a extended partition and place linux on it. Would this work:

Partitin table:
1) EFI 
2) OSX
3) Windows XP
4) Extended partition --> 
logical partition 5)ext3 with Linux system
logical partition 6)an extra NTFS Partition

---

### Post by WA_Garrett on 2009-07-03
I've heard that windows can't handle anymore than 4 partitions on a single volume and that it likes to be on the last partition. I've got triple booting working on my macbook but my partition scheme only has 4 partitions.  I have EFI is my first partition, OS X on the second, Linux on the third and Windows on the 4th. And yes I have no Swap partition for linux. I haven't tried to do more than 4 partitions though, but it might be worth a try. So go ahead a give it a shot. Worst thing that could happen is that it won't work and then all you would have to do is redo the installations with 4 partitions. I would like to know if your scheme would work though.

---

