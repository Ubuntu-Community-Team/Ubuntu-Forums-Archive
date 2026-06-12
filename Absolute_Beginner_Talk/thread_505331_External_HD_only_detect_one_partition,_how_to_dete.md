---
title: "External HD only detect one partition, how to detect the other partition ??"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by ChenJianYi on 2007-07-20
Hi, I have an external HD and my HD has 2 partitions.
When I plugged this, ubuntu only detect the first partition.

How to detect and mount the other partition ?

---

### Post by Midahed on 2007-07-20
Hello,

What did you use to set-up the partitions on your external drive?  Was it something like gparted or one of the other Linux partitioning tools?

Can you connect the external drive and then open a terminal session and run the command fdisk -l and post the output.  While you have the terminal session open, can you also run the command cat /etc/fstab and post that as well.

Mike

---

### Post by AlexenderReez on 2007-07-20
try this--->

> [http://ubuntuforums.org/showpost.php?p=3047936&postcount=2](http://ubuntuforums.org/showpost.php?p=3047936&postcount=2)

---

