---
title: "I Need install help, mainly partitioning (links are A ok)"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Cudzooking on 2007-10-17
Hey, complete beginner here.
I have plenty of computer know how, but partitioning in Ubuntu escapes me.
I'm currently running of the live CD for Feisty Fawn, and would like to install through this.
Unfortunately, I can't set up partitions, and there are already 3 used. The disk partitioner tells me that only 4 can be created, unless I use an ?extension? Could someone tell me what partitions sizes to use and what type?
I'm currently running Vista on a Dell Dimension e521, with a 250 GB hard drive. I would like the partition(s) to be under 50GB, but if that's not possible, just throw around whatever!
Thanks for any and all help:popcorn:

---

### Post by Pumalite on 2007-10-17
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by jingo811 on 2007-10-17
> **Cudzooking said:**
> Hey, complete beginner here.
......
Unfortunately, I can't set up partitions, and there are already 3 used. The disk partitioner tells me that only 4 can be created, unless I use an ?extension? Could someone tell me what partitions sizes to use and what type?
...

You can only have 4 Primary partitions on one disk thus your 4th will have to be Extended in order to make an infinite amount of Logical partitions.

10 GB for................... **[SIZE="4"]/[/SIZE]** = [ (root) partition ]
1 GB for...............**swap** [ partition ]
As much GB as possible for your personal data in................... **/home** [ partition ]

---

### Post by overdrank on 2007-10-17
> **Cudzooking said:**
> Hey, complete beginner here.
I have plenty of computer know how, but partitioning in Ubuntu escapes me.
I'm currently running of the live CD for Feisty Fawn, and would like to install through this.
Unfortunately, I can't set up partitions, and there are already 3 used. The disk partitioner tells me that only 4 can be created, unless I use an ?extension? Could someone tell me what partitions sizes to use and what type?
I'm currently running Vista on a Dell Dimension e521, with a 250 GB hard drive. I would like the partition(s) to be under 50GB, but if that's not possible, just throw around whatever!
Thanks for any and all help:popcorn:

Hi this thread may help
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

In short to have more than 4 partitions on one drive one of the partitions will need to be a extended partition. And within that extended partition you may create more partitions. Good luck!

Edit TO late. :)

---

### Post by Cudzooking on 2007-10-18
Thanks all, I hope to attempt this in the very near future:KS

---

### Post by Cudzooking on 2007-10-26
Hey, It worked, THANKS ALL:guitar:

---

