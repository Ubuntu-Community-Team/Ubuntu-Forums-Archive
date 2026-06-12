---
title: "Problem with Partiton Manager, when Installing Ubuntu"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Elad on 2007-05-18
Hello All,

First of all, i want to say this is the seconed time im try to install Ubuntu,
Before 6 months i try to install it and i removed all my disk!!!

The problem is the partition part, i dont know what to do.

My questions is:

1. Which file system is most recommend?. ext2, ext3, ntfs, etc..?
2. I have 3 disks, C:\, D:\, E:\. C (20GB,10GB free) is the windows partition, D (80GB,31GB free) with all my important data, and E (20GB) is empty.

Now i want to install Ubuntu on E, but he says me that i need a partiton with Swap.
What i need to do?
If i select C to swap, my data can to removed.

What is the most recommend step for me to do?

And someone can give me a full good tutorial how to install Ubuntu, with Screenshots.

Thanks all very much!

---

### Post by theicyj on 2007-05-18
Create a swap partition on E that is, as a general rule of thumb, twice the size of your RAM.  Format the rest of E with ext3, and install ubuntu on that.

---

### Post by overdrank on 2007-05-18
> **Elad said:**
> Hello All,

First of all, i want to say this is the seconed time im try to install Ubuntu,
Before 6 months i try to install it and i removed all my disk!!!

The problem is the partition part, i dont know what to do.

My questions is:

1. Which file system is most recommend?. ext2, ext3, ntfs, etc..?
2. I have 3 disks, C:\, D:\, E:\. C (20GB,10GB free) is the windows partition, D (80GB,31GB free) with all my important data, and E (20GB) is empty.

Now i want to install Ubuntu on E, but he says me that i need a partiton with Swap.
What i need to do?
If i select C to swap, my data can to removed.

What is the most recommend step for me to do?

And someone can give me a full good tutorial how to install Ubuntu, with Screenshots.

Thanks all very much!


HI this link may help!
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Good luck!

---

### Post by Happy_Man on 2007-05-18
You want to create one big / partition, formatted ext3. You then want to have a 512 MB swap partition, formatted swap. 

To do this, from the Ubuntu installer, choose to manually partition. Delete E: and so you now have 20 GB of blank space. Right-click on the blank, choose new, and create a 512 MB partition, format it swap. Right-click on the rest of the unformatted space, let it use the rest of the area, format it ext3. 

There you go, you're done! Apply the changes and move on with the installer.

---

### Post by Inxsible on 2007-05-18
Are you planning to keep Windows?
You cant have swap on C then. 
 
Also, if you want to install Ubuntu on 'E'... you would first have to unmount the drive from windows. Ubuntu will not format a mounted drive. In other words, go to Disk Management and simply right click on drive E and then select Delete Volume.
 
This will make the space unallocated..where you can then install Ubuntu.

---

### Post by Elad on 2007-05-18
I want to select Windows or Ubuntu.
Im not want to remove windows.

---

### Post by Inxsible on 2007-05-18
Since your E is empty, Delete the Volume from Windows. Then you will need to make an Extended Partition on it and create *atleast* 2 Logical Partitions on it one for / and another for swap. Most people also prefer to have a separate /home partition. So in all 3 partitions.
 
Use these links for a detailed explanation:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Elad on 2007-05-18
2Inxsible

Thank you, im start understanding you.
But i have a problem.
I remove E, now as you say the space is unallocated. When im going to Ubuntu installer what i need to choose? To manage the partitions i need to select manually and this will replace me the Windows with Ubuntu, and im not want it.

And what about the Swap partition? Where im install it? I need to create another partition or i can to install it on C:\Windows, without problems?

Thanks!

---

### Post by Inxsible on 2007-05-18
No do not install anything on C:

You will have to create an Extended Partition on the unallocated space and then create  3 logical partitions on it. for  / (root) /home and swap.

On Gparted when you create the first partition, select Logical instead of Primary.


That should do it for you !

---

### Post by seshomaru samma on 2007-05-18
first - back up all your data on Windows
second - make sure you understand how linux sees partitions (ie. forget C, D and E .read the link Inxsible gave you carefully)
third - choosing manually will not earase windows - it will allow you to choose which partition to install into.

i suggest this:
are you using a live CD?
before you click on install open a terminal (look at the top panel, Applications &#8594; Accessories &#8594; Terminal)
**copy paste** this command :
```
sudo fdisk -l 
```
this will show you how linux sees your disks
paste the output here and we will explain it,
remeber in the linux partitioner there are no C, D or E
it's all hda1, hda2 or whatever...

---

### Post by Elad on 2007-05-19
2Inxsible

What you mean GParted?
This program is for Linux.
You mean that i use it from the boot Ubuntu CD?

And i have a question, in the installer what to choose? Guided, manually..?

---

### Post by Sef on 2007-05-19
> What you mean GParted?
This program is for Linux.
You mean that i use it from the boot Ubuntu CD?

[GParted]("http://gparted.sourceforge.net") is a partitioner.  It is both a stand alone disk, and it is on the Ubuntu's install cds.



> And i have a question, in the installer what to choose? Guided, manually..?

GParted has has a gui interface, so you can use your mouse to help partition.

---

