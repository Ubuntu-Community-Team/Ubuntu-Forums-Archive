---
title: "[SOLVED] Drive Partitioning. . ."
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by bobd104 on 2007-12-21
My HD is 60Gig, I've partitioned maybe too many times and now I have Partition C(Primary OS installed) and then I have Partitions F & G (Each approx. 8 Gig).  I would like to either merge F & G to a single 16 Gig partition or merge F&G partitions with the primary "C"?  Can I use GPARTED for this?  If not, are there any suggestions?  Thanks. . .

Bob D.

---

### Post by overdrank on 2007-12-21
> **bobd104 said:**
> My HD is 60Gig, I've partitioned maybe too many times and now I have Partition C(Primary OS installed) and then I have Partitions F & G (Each approx. 8 Gig).  I would like to either merge F & G to a single 16 Gig partition or merge F&G partitions with the primary "C"?  Can I use GPARTED for this?  If not, are there any suggestions?  Thanks. . .

Bob D.

Hi and gparted is a great utility and you can do a lot of things with it.I believe you can delete the partition that you describe and then create a new partition. Remember that you can have 4 partitions to a drive and then the 4 th will have to be a extended partition and then you will be able to create more partitions.

---

### Post by overdrank on 2007-12-21
Oh now some one has to contradicted me :)

---

### Post by eternicode on 2007-12-21
> **bobd104 said:**
> I would like to either merge F & G to a single 16 Gig partition or merge F&G partitions with the primary "C"?  Can I use GPARTED for this?

In short, yes, GParted can do this easily.

In long, no GParted cannot "merge" partitions, meaning combine the data from both partitions into a single partition with all files intact.  You will want to:

1) move the data (files) from F and G to C
2) delete F and G
3) resize C to fill all empty space.

Of course, you will (as always) want to backup/move any data from F and G (and C) before beginning the project.

> **overdrank said:**
> Remember that you can have 4 partitions to a drive and then the 4 th will have to be a extended partition and then you will be able to create more partitions.

I've heard a drive can have no more than 4 primary partitions, so the 4th will be an extended partition; then the extended partition can have up to 64 logical partitions.  Not sure how accurate this is, but it's the most concrete thing I've heard ;)

---

### Post by overdrank on 2007-12-21
:guitar: Thanks and a good link to partitions it here
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by bobd104 on 2007-12-22
Thanks to all for the answers.  Deleting F&G and then resizing C to absorb all remaining space was the right answer. . .  If in the VISTA OS environment, the built in disk management console also will accomplish this task, however, you must follow a logical sequence to be afforded the appropriate menu selections otherwise your choices become grayed-out and very limited?  It's tricky but if done correctly works very well.

So now, how does one go about closing a post. . .

Bob D.

---

### Post by jken146 on 2007-12-22
Thread tools > mark as solved

---

### Post by bobd104 on 2007-12-22
Can't locate thread tools? ? ?

---

### Post by eternicode on 2007-12-22
[attach]54006[/attach]

---

