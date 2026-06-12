---
title: "How much partitions to create on second hard drive"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by sjieke on 2006-11-23
Hello,

I have a second harddrive (250 GB) for data storage. At the moment there are 4 partitions on it:
   * partition 1: 90 GB -> 60% usage
   * partition 2: 90 GB -> 90% usage
   * partition 3: 35 GB -> 10% usage
   * partition 4: 35 GB -> 10% usage

The problem is that partition 2 always is full of stuff and the others have plenty of room. So I thought of repartitioning the drive with only 1 partition.
My question is if this is a good idea to have one big partition of 250 GB, or would it be better to have 2 or more?

Thx,

Greetz
Sjieke

---

### Post by Bachstelze on 2006-11-23
If you don't need several partitions, why create them ?

---

### Post by aysiu on 2006-11-23
If it's all just data, one big 250 GB partition is a great idea, especially if it's not FAT32 (i.e., if it's Ext3 or NTFS).

---

### Post by sjieke on 2006-11-23
Thx, for the fast reply's. I'm planning to use xfs as filesystem. Going to start at it as soon as I get home...

---

### Post by Antarctica on 2006-11-23
Look at it this way:  you have 4 glasses of milk.  Why be so frustrated over the second glass being full when you can just enjoy one BIG glass of milk?  Hehe, think of it that way.

---

### Post by Circus-Killer on 2006-11-23
it all really depends on you and what you want to use the different partitions for. i mean you could have a seperate partition for media files. a partition for your database data. etc. etc.

personally, i have 1 x 40GB and 1 x 80GB

the 40 GB looks like so:
/boot = 150MB
swap = 1GB
/ = rest of disk (+-37GB)

the 80GB looks like this:
/home = whole disk

now thats my own setup, and even like that my / partition is way overly large, but at least i dont have space problems. :P

whatever works for you i guess, thats whats recommended.

---

### Post by aysiu on 2006-11-23
I think having a separate partition for /home or /boot can be useful, but if they're just different types of files (media, database, pictures, etc.), they can be on one partition but in different folders.

---

