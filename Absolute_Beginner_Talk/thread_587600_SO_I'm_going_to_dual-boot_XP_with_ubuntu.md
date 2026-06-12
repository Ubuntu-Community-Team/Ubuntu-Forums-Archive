---
title: "SO I'm going to dual-boot XP with ubuntu"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2007-10-22
I have a question, though. MY hard drive has 3 primary partitions:
EISA Configuration, OS Partition, and Recovery Partition

If I understand right, you can only have 3 primary partitions. So I'll have to delete the EISA and Recovery partitions, shrink the OS partition, then create a swap area partition and ext3 partition . Is the EISA configuration important? Or can I delete it?

---

### Post by Sef on 2007-10-22
You can make a logical partition.  You can have as many logical partitions as you want.  When making the partition, you will be given the option of primary or logical, so just change the from primary (the default) to logical.

---

### Post by overdrank on 2007-10-22
> **piratesmack said:**
> I have a question, though. MY hard drive has 3 primary partitions:
EISA Configuration, OS Partition, and Recovery Partition

If I understand right, you can only have 3 primary partitions. So I'll have to delete the EISA and Recovery partitions, shrink the OS partition, then create a swap area partition and ext3 partition . Is the EISA configuration important? Or can I delete it?

HI and yes you can have 4 partitions to a drive, What size drive are we speaking of GB?
EDIT to slow lol

---

### Post by piratesmack on 2007-10-22
The hard drive is like 200GB so I got plenty of room
I always thought you couldn't install OSes on a logical partition, only primary

---

### Post by aidanr on 2007-10-22
You can delete the EISA Configuration partition, it's probably just recovery/trouble shooting tools used by the vendor when you send it in for repair. But seeing as you're putting Linux on you probably won't be sending it in for support and if you do they probably wouldn't look at it anyway. So you can delete it, but make sure your windows boot.ini properly reflects any changes to the position of the windows partition.

---

### Post by overdrank on 2007-10-22
> **piratesmack said:**
> The hard drive is like 200GB so I got plenty of room
I always thought you couldn't install OSes on a logical partition, only primary

Yes that is why Sef stated you create the logical partition then create partitions within it. :)

---

### Post by piratesmack on 2007-10-22
And I can do this with the ubuntu install CD?

---

### Post by overdrank on 2007-10-22
> **piratesmack said:**
> And I can do this with the ubuntu install CD?

HI and yes you can, gparted is located under system, administration and this is where you can resize and create your partitions.

---

### Post by piratesmack on 2007-10-23
> **overdrank said:**
> HI and yes you can, gparted is located under system, administration and this is where you can resize and create your partitions.

Well something went wrong and I lost all data on my XP partition. So I guess I'll delete all partitions, install XP on a 150gb NTFS partition and use the remaining 50GB for ubuntu. Thanks for your help

---

