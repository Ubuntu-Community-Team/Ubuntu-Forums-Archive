---
title: "Theres Not Enough Disk Space!"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2006-09-24
i wan't to install ubuntu on partition C:. The capacity of the drive is 20 GB, i have 8.8 GB free space. What ever i do it says that i don't have enough disk space.What is your suggestion?;)

---

### Post by crokett on 2006-09-24
How is the drive currently partitioned?  Do you have 8GB of free space on an existing partition or you have 8Gb of space on the drive that you can create a partition in?

---

### Post by Sterbik on 2006-09-24
I have 20GB of space but 10GB is used. I thought that i could install the OS to drive D: because i have plenty of free space. I'm worried, if i do something stupid, my music's and other document's can go away. Before i forget: why do i have to do with mounting. There are lot of options. I have read it all in the HELP link, but the answeres not really helped... I just want to install an operating system:, so i could choose when to use windows or linux.

---

### Post by Linducker on 2006-09-24
Something must be wrong since ubuntu needs only 5 GB of HD space.

 Is the space formated?

---

### Post by crokett on 2006-09-24
Ok.... so again, how is the drive partitioned?  The drive is 20GB and is one 20GB partition with 10GB of free space? The drive is 20GB with 2 10GB partitions?  The drive is 20GB with 1 10GB partition and 10GB of free space?  

In any case, Ubuntu really needs its own partition formatted to ext2 or ext3.  So if you have a drive that has no space to create partitions you need to either resize the existing partitions  with gparted so you can create one, or you need to get another dive.

---

### Post by Sterbik on 2006-09-24
I don't really understand your question...
drive D: is an excisting drive like C:. I don't want to mess up with reformatting and stuff.

---

### Post by Sterbik on 2006-09-24
My HD is 80GB. C: has 19.5GB, D: has 54.9.

---

### Post by Sterbik on 2006-09-24
So... If i want windows with ubuntu, i have to refomat a drive and put it there?

---

### Post by siminone on 2006-09-24
What you need to do is defrag D drive to be on the safe side that nothing gets accidently deleted. 

When installing Ubuntu, resize the D Drive. In the new space create a new partition for Ubuntu.

---

### Post by Sterbik on 2006-09-24
How to resize the drive?

---

### Post by bodhi.zazen on 2006-09-24
[How to install Ubuntu](http://www.psychocats.net/ubuntu/installing.html)

Defragment as above first.

---

### Post by Sterbik on 2006-09-24
i had defragmented my D: drive with diskepper 9...What's next?

---

### Post by CatKiller on 2006-09-25
From the link that bodhi gave you:> The third option is ideal for people who know a little bit about partitioning and mounting of partitions. You want to resize the partition that **isn't** hda1 (your C: drive). Your D: drive is **probably** called hda5. That is the partition that you want to resize.

---

### Post by Sterbik on 2006-09-25
yes.  I wil now download partition magic from Powerquest. I just have to create a new partition ?

---

### Post by CatKiller on 2006-09-25
> **Sterbik said:**
> yes.  I wil now download partition magic from Powerquest.

You don't need to use Partition Magic, although you may if you wish. The Ubuntu installer already has the ability to edit your partitions.

> I just have to create a new partition ?

No. As I understand it from what you've said previously, your hard drive contains two partitions that between them take up all of the space on the hard drive. You need to make the second partition (your D: drive in Windows) smaller to make space for Ubuntu to install in. This is the critical step.

Once there is unallocated space on the hard drive, the Ubuntu installer can do all the rest for you automatically.

---

