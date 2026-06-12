---
title: "partitioning sata drive"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by jtnoob on 2007-04-27
My system has a 160gb sata drive and a 120gb ide drive. I am currently using the ide for storage. I would like to partition the sata so I can use most of it for storage as well.  When I install feisty fawn 7.04, it sees my sata as a scsi and seems to use the whole 160gb. How do I set up my sata drive with an Ubuntu os partition and a large storage parition?

Thanks

---

### Post by johnnymac on 2007-04-27
So...if you try to fdisk it manually does that work?

---

### Post by whee on 2007-04-27
Did you let Ubuntu create your partitions automatically during installation or did you do it manually during installation?

---

### Post by jtnoob on 2007-04-28
I have tried it both ways. Perhaps I didn't understand what I was looking at. I set a partition to about 15gb for the OS. Then I set 2gb for the swap. I wasn't sure what to set the storage partion to, and I forget how I did set it.

---

### Post by jtnoob on 2007-04-28
You'll have to excuse my newbness, I don't think I have used fdisk to create partitions before. I have done it on a windows installation and with partition magic, but I'm not sure how to do it with fdisk. Here is what I get when I type fdisk (I hope this helps):
jpt@jpt-desktop:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by AlexenderReez on 2007-04-28
> **jtnoob said:**
> I have tried it both ways. Perhaps I didn't understand what I was looking at. I set a partition to about 15gb for the OS. Then I set 2gb for the swap. I wasn't sure what to set the storage partion to, and I forget how I did set it.

swap partition is to support ram (random access memory ) ...but it is really waste of partition if swap more than 1 gig...because if you have a high ram...actually you just need really small space... 

my swap only 600mb...but i the highest i have use only 3%(while running beryl + rythmbox+ firefox+ running upgrade in synaptic)  ....my ram is 1gig only ,,,

---

