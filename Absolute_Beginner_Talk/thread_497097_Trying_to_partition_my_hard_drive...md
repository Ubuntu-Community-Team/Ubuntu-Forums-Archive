---
title: "Trying to partition my hard drive.."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by karmakaze11 on 2007-07-09
I'm trying to install Ubuntu, and I got to the part where I select a partition (I want to dual boot with XP) and I select the 11Gb fat32 partition I made for Ubuntu, then I get the error message: No root file system is defined. Please correct this from the partitioning menu.
How do I do this?

---

### Post by bobplano on 2007-07-09
you'll want to use ext3 to start off with. next you need to make 2 partitions one of them is for root and the other is swap. for root make a partition of any size, but a recommended size is between 5-10gb. the other partition is swap, so just format that as a swap partition.

---

### Post by oilchangeguy on 2007-07-09
> **karmakaze11 said:**
> I'm trying to install Ubuntu, and I got to the part where I select a partition (I want to dual boot with XP) and I select the 11Gb fat32 partition I made for Ubuntu, then I get the error message: No root file system is defined. Please correct this from the partitioning menu.
How do I do this?

read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Happy_Man on 2007-07-09
Right.... first off, you'd be better off using an ext3 format filesystem for your Ubuntu / partition. Things will go a lot smoother when you try to do major stuff, trust me. 

Now, do you see the column where it shows entries like "/media/sda1", etc.? Find the partition you want to assign Ubuntu to, and right-click it. Choose "edit partition" and from the drop-down list, select /. Then select OK and keep going.

---

### Post by sab0403 on 2007-07-09
There's no drop down list that lists "/" as an option. There is, however, an option named "Mount Point". There you have to put the slash (just the slash, no quotation marks).

Good luck!

---

### Post by karmakaze11 on 2007-07-09
Thanks for your help, guys. It is now installing, and hopefully there won't be any more problems. Cheers ^_^

---

