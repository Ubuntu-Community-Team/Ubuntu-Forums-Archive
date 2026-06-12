---
title: "[SOLVED] creating a vfat partition within ubuntu"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by djules26 on 2008-04-17
good day to all!

tried installing ubuntu 7.10(desktop) a while ago and i got an error in the partitioning part. i have a 160g hard disk drive and tried to partition it in this manner(i chose the manual not the guided partitioning).

partition1 /(root) as ext3
partition2 /home as ext3
partition3 /windows as vfat ---------> This gives me an error!
partition4 /swap as swap

installation does not proceed...it returns back to the partitioning part.

what i want to do is make at least one  vfat  partition so that i can share it thru my network and enable it for read/write and make it fully accessible with windows 98, since the other computers on my network are running windows 98.

need your help...thanks.

---

### Post by chewearn on 2008-04-17
You can create the vfat partition separately before installing ubuntu using a partition tool.

---

