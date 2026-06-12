---
title: "What should I do?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Elias~ on 2007-06-16
So, I had Windows Pro.

I tried Linux.

I partitioned my drive.

Now Windows is broken.

My drive is split in half.

I like Linux a lot more then Windows.

How would I go about deleting Windows completely and adding that part of the hard drive to my Linux OS so it has more space?

---

### Post by aidanr on 2007-06-16
download the [gparted live cd]("http://gparted.sourceforge.net/livecd.php"), you can delete/resize partitions

---

### Post by Elias~ on 2007-06-16
Thats the easiest way?  Will it delete Windows too?

---

### Post by aidanr on 2007-06-16
yes it will delete the windows partition, it supports fat16, fat32, ntfs

---

### Post by Elias~ on 2007-06-16
Thanks! :D

---

### Post by aidanr on 2007-06-16
by the way, you will have to remove the grub entry manually

sudo gedit /boot/grub/menu.lst

---

### Post by Elias~ on 2007-06-16
Thanks.  I think I just deleted Kubuntu...  Oops.  X.x  I plan on going to Ubuntu for wireless anyways.  All my partitions are unallocated, can I install Ubuntu on my one big unallocated partition?

---

### Post by Elias~ on 2007-06-16
Oh and by the way, I get grub error 22 now that everything is unallocated, is that normal? X.x

---

### Post by bobplano on 2007-06-16
you can install ubuntu on a big partition but you need at least another partition for swap. its ok for you to be getting the grub error because there aren't any OSes installed so obviously it can't find any

---

### Post by Elias~ on 2007-06-16
Okay, I'll just put in Ubuntu and see if it works.  There were 2 big and 2 small partitions.  I just deleted the two big ones and left the smaller ones alone.  And what do you mean by "swap"?

---

### Post by bobplano on 2007-06-17
ubuntu needs a partition for itself and this is the main partition. then, just in case your computer doesn't have enough ram, or you put it in hibernate or suspend, ubuntu needs a "swap" partition to store extra info from the ram if you don't have enough. if you suspend of hibernate your computer, the ram dumps everything it has into the swap partition. even if you don't suspend your computer, and you have enough ram, you still need a swap partition or ubuntu won't install

---

### Post by steveneddy on 2007-06-17
If you are going to reinstall, then just put the disc in and tell it to use the whole disc and add a swap partition.

---

