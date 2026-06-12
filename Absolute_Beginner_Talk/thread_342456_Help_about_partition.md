---
title: "Help about partition"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-01-20
Hi

I've got an Acer Aspire 3860 (laptop computer) that I want to have Ubuntu on with dualboot. When I bought the machine, there were 3 partitions on it:

C: - a normal place like every other Windows computer
D: - a kind of a recovery place where Acer got the files for reinstalling Windows etc.
PQSERVICE - I don't know what this is, I can't do anything to it. It says something about "EISA"

I've got an harddrive on 40 GB. The C and D is almost 50-50, and the last one 4 GB.

In Gnome Partition Tool Manager I have taken this screenshot.

Hda1 = PQSERVICE
Hda2 = C:
Hda3 = D:

Now I want to make the D a bit smaller, for example 8 GB in stead of 17 GB. Then I'll add a new partition for Ubuntu.

But here I am bit unsure. I have heard something about that you can only have 4 big partitions, and the extra swap partition for Ubuntu counts as one. Then I'll got 5 ... is this a problem or what?

Please help me
Thanks!
Sorry for my bad English (:

---

### Post by pebo on 2007-01-20
What you will have to do is resize hda3 in gparted. (After having defragged and done a back-up;)  ). You'll then have to create a new partition for your ubuntu in the free space. You are right that you are only allowed 4 primary partitions, but when you create the linux partition, create it as an extended partition. Inside this you can create as many partitions as you need, eg for swap and /home.
hth

---

### Post by Sef on 2007-01-20
To Dual boot, read these sites:

From the Live CD, [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

From the alternate cd, the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").

---

### Post by Wikzo on 2007-01-20
Thanks for the help :)

> **Sef said:**
> To Dual boot, read these sites:

From the Live CD, [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

From the alternate cd, the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").
I have already read both of those. My quistien isn't how to dualboot, but just about my harddrive and partions.

---

### Post by Wikzo on 2007-01-20
Oh, and can anyone tell me what lba stands for? (see the screenshot)

---

### Post by housam on 2007-01-20
Read [this site]("http://community.linux.com/howtos/Partition/fdisk_partitioning.shtml") it may help to know about partitioning.

---

### Post by qpieus on 2007-01-20
> **Wikzo said:**
> Oh, and can anyone tell me what lba stands for? (see the screenshot)
Logical block addressing
[http://en.wikipedia.org/wiki/Logical_block_addressing](http://en.wikipedia.org/wiki/Logical_block_addressing)

---

