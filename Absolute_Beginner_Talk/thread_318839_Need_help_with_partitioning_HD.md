---
title: "Need help with partitioning HD"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by r0nin on 2006-12-14
I've been trying to help a mate install Ubuntu on his PC. I've attached a screenshot of his current partitions.
We want to create 4 new partitions for Ubuntu. Swap (1gb), /root (6gb), /home (4gb) and a 3gb FAT32 partition to swap files between WinXP and Ubuntu. The installer has been giving us hell about only being alowed to have 4 primary partitions and not being able to install on an extended partition. Could you guys please tell us how to partition the HD correctly? We've been trying for two hours now and I cannot figure it out. It's especially annoying as I've done this many times before, I just cannot get down to the problem this time though.
Thanks.

---

### Post by bodhi.zazen on 2006-12-14
You can only have 4 primary partitions.

ONE of those partitions can be an extended partition.

Right now /dev/sda2 is an extended partition so the gray space at the far right can be partitioned as a SINGLE PRIMARY partition, but you can not further subdivide it ....

Solution:

Delete
sda3 (copy the data to your NTFS partition temporarily if needed)

sda6
sda7
sda8

Resize sda2 to take up the entire HD

Add back the partitions you need to sda2

You can re-create sda3 within sda2 if you like.

---

### Post by ]Nbx*cmD[ on 2006-12-14
You'll need a / partition for the system!!

---

### Post by r0nin on 2006-12-14
So I can install Linux (or any other OS) on an extended partition created in Windows?

---

### Post by bodhi.zazen on 2006-12-14
Should be able to ....

---

### Post by drphilngood on 2006-12-14
This should help:

[psychocats-Partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Good luck!

---

