---
title: "partition problem"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by frrobert on 2007-06-22
I went to start my laptop today.  It started and when it was going through bootup it ran an check disk on my linux partition.  It had an error and told me to do a manual check disk on the partition.  I followed the instructions and it said could not read the super block on the partition.  Then went nuts and locked up.


If I start the machine now it says Grub error 17.

It is a toshiba laptop running Drapper Drake

Partition 1 is Windows XP
Partition 2 is my Linux partition including home.
Partition 3 is a swap
Partition 4  is an EXT3 partition for data.

Partition 2 is the the corrupted partition.

3 questions

1.  Is there any way to retrieve that partition?  
I tried using the live CD but it was labeled unknown file type.  If I can't no big loss the only data on it was my email and my palm pilot data and I backed up my email the other day, so I only lost a handful of emails and the data is still on my palm.


2.  Is the most likely cause of the Grub error the unreadable partition.  Can I edit the grub file so I can still boot into windows?

3.  Most likely cause software related or a bad spot on the hard drive?  The drive is almost 3 years old.  I do have a warranty on the laptop that expires in August so if it is a bum drive I want to get it swapped out before then.


Thanks

---

### Post by gn2 on 2007-06-22
Have you performed any partitioning jobs while booted into Windows which may have affected the size of the problem partition 2?

If you have it's possible that has broken things.

Checkout the Hermanzone link in my sig for lots of useful info from the MBR link down to the Super Grub link.
It's very comprehensive and well worth a read.

---

### Post by frrobert on 2007-06-22
I can't even remember the last time I even booted into windows and I've never used a partition tool since I installed linux

---

### Post by az on 2007-06-22
You can use parted to rescue your partition table.  See here:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by frrobert on 2007-06-23
Thanks for all your help.  It looks as it the drive is dying.  Got it fixed and it is having problems again.  So time to send it in again.

---

