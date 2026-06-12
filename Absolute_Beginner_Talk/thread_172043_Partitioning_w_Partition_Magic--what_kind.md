---
title: "Partitioning w/ Partition Magic--what kind?"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by CUSTADD on 2006-05-07
I have a laptop hard drive partitioned with 2 Primary partitions and one Logical partition.  I have XP on one of the Primary partitions and I want to use the other one to install Ubuntu on. The Logical partition, a FAT32 partition, is for saved files that I want to access from Windows or Ubuntu.

I want to partition the Ubuntu Primary partition using Partition Magic, then install Ubuntu. 

The question: do I make the Ubuntu partition a Linux Ext2 or Linux Ext3 (the options Partition Magic provides for Linux)?

P.S. Many thanks for these open source programs to break the Mi cro soft addiction and for these forums to help us make the transition!

---

### Post by Gannin on 2006-05-07
If you were going to choose between ext2 and ext3, I would go with ext3, because it is a journaled file system that is built upon ext2 (and is therefore still compatible with it) but is a lot safer and has much faster recovery than ext2.

However, when installing Ubuntu, it does have its own partitioner that you can use if you'd like, instead of Partition Magic.

---

### Post by CUSTADD on 2006-05-07
Thanks for taking the time to help! 

I am familiar with Partition Magic--that's the main reason I want to use it. What are the differences between using PM and Ubuntu's own partition capability? If using Ubuntu requires any special knowledge to do, I probably should use PM, but if Ubuntu is pretty intuitive and does most everything automatically, maybe I could use it.

---

### Post by WolfJay_83 on 2006-05-07
I't doesnt realy matter which you use to partition your hard drive.  If you leave the area as unpartitioned, you can tell the ubuntu partitioner to use the "unused space".  Otherwise, partitioning with PM, you can select to install ubuntu to the ext3 partition.  I would suggest just leaving it as unpartitioned as the ubuntu installer is very easy to use.

Note: you will need a swap partition.  Either leave empty space (twice your ram, up to about a gig max) or just use the ubuntu installer to create an ext3 partition for the system and a swap partition.

hope this helps

---

### Post by Gannin on 2006-05-07
It doesn't require any extra knowledge really.  But it is an integrated part of the installation process, so there is the benefit of it being part of the natural flow of things.  Even if you use Partition Magic, I think you'll still have to use Ubuntu's partitioner a little bit, to tell it what partition you want to use as / (root), and what partition you want to use as the swap partition.

As always, make sure you backup all the information on the drive you're working on.

---

### Post by Sutekh on 2006-05-07
Partition Magic and Ubuntu may not get on so well.  The Ubuntu partitioner is fairly straight-forward.

If you want an alternate to Partition Magic and the Ubuntu Installer try the [GParted LiveCD](http://gparted.sourceforge.net/livecd.php)

---

