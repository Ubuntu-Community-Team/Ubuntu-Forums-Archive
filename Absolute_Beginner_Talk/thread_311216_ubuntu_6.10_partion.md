---
title: "ubuntu 6.10 partion"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by cessna_89702 on 2006-12-02
Hey I burned ubuntu 6.10 to the disk and i have it working fine off the disk. I havent installed it yet because im not sure how i can make a big enough partion. I have windows xp installed right now and would like to set up a dual boot. How do I create a big enough partion for Ubuntu?
And a friend told me it wont run wireless internet off the disk/is that true?

---

### Post by PriceChild on 2006-12-02
*moved*

---

### Post by Sef on 2006-12-15
> I have windows xp installed right now and would like to set up a dual boot. 

Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by amaroKer on 2006-12-15
There is no reason that you should not be able to get onto the internet with the live cd.  If it does not work, either you need to configure it, or you need drivers.  Some system specs are always helpful...

As for the partitioning, you neglected to mention how big your hard drive is in the first place.  Again, details my friend.  You can generally get away with a 5GB type: "ext3" partition to install Ubuntu on, but I wouldn't do it with less than 10.  You also need ~1GB type: "linux-swap" partition, and you need to tell the installer that you want to use these partitions after you create them.

---

