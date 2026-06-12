---
title: "Shrink Partition"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by Magellan on 2006-02-04
I allows the install program to free up soem space and create a new partition for installing Ubuntu.

It took all the free space on my disk and create 2 partitions from it.  A 21G one for the file sysmte, and a small one for swap.

I would like to shrink the 21G partition down to about 5G and put the other 15G in a FAT32 partition to share with Win2k.

Can someone give me some tips on this.  I'm not a total newbie to computing, but am new to linux.  

I have a Live CD if I need to boot into that. 

Thanks,

James.

---

### Post by alamba on 2006-02-04
Boot with the live cd. From the command line type:

sudo gparted

Highlight the partition and shrink away!

Akshay

---

