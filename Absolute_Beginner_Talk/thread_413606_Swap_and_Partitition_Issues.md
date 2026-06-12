---
title: "Swap and Partitition Issues"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Acglaphotis on 2007-04-19
Hi

I wanna install Feisty (Currently on dapper, mainly because of the hardware support) but i want my home directory in another partition, but swap is keeping me from doing that because i already have installed vista and i have a recovery partition THAT IS VERY IMPORTANT because vista tends to screw up my pc, or i did something i wasnt supposed to do and else.

So i want something like this

Vista|Recovery|Home|Ubuntu

But because i can only make 4 partitions i can only get something like this

Vista|Recovery|Swap|Ubuntu

So, my question is , can i put swap on an extended partition? Because swap is really annoying me.

Acgla

---

### Post by Skrynesaver on 2007-04-19
Yes you can put swap on an extended partition, however (there's always a "howeve"0, and this is a trivial point really but outer tracks on a disk are faster so giving swap as low a partition number as you can is, barely, worthwhile.

---

### Post by az on 2007-04-19
> **Acglaphotis said:**
> 
But because i can only make 4 partitions i can only get something like this

Vista|Recovery|Swap|Ubuntu

So, my question is , can i put swap on an extended partition? Because swap is really annoying me.

Acgla

Why make a seperate home?  Just make your life easier and take the default partitioning schene which would be root with home on one partition.  You won't run out of space that way and you don't have to muck around with partitionning.  It's just as easy to backup a home folder as preserve a home partition, it's simpler, in fact.


> **Skrynesaver said:**
> Yes you can put swap on an extended partition, however (there's always a "howeve"0, and this is a trivial point really but outer tracks on a disk are faster so giving swap as low a partition number as you can is, barely, worthwhile.

Outer tracks are not faster.  They spin by faster (greater velocity) but there are more blocks.  It is exactly the same.  And drive seeking takes up the most time.  It is actully more efficient to have your swap and root folder as close as possible, but even that is pretty much insignificant.

---

