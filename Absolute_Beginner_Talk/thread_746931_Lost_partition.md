---
title: "Lost partition"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by aduplat on 2008-04-06
hi to all,

I have a huge problem. I installed Ubuntu in an external hard drive which is divided into two  partitions. In one partition I have a backup for windows and in the second Ubuntu. In this hard drive I installed Grub and I don't know why I have lost the partition for Ubuntu. What do I do to recover it?

Thanks,

Alfredo

---

### Post by Sef on 2008-04-06
Use the Live CD, then Applications > Accessories > Terminal

then type this code:

```
sudo fdisk -l
``` Small L

Copy and paste the results here for that hard drive.

---

