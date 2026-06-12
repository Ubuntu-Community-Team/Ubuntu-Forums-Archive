---
title: "partition advice"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Comcon on 2007-06-07
Hallo,
How do i make partition for Linux with Gparted?
Thanks

---

### Post by joselin on 2007-06-07
First you must resize the partition you have and then, you will be able to add a new one.

---

### Post by Inxsible on 2007-06-07
Its an ntfs file system. It also has the boot flag on it, so Windows is installed.
 
Do you want to keep Windows and have a dual boot ?
 
Or remove Windows completely and go solo with Ubuntu?

---

### Post by Inxsible on 2007-06-07
If you are gonna keep Windows, you should boot into Windows and do a couple of defrags on the drive before you create partitions with GParted.

---

### Post by Comcon on 2007-06-07
no i would like to keep windows.I want to have dual boot
Thanks again

---

### Post by Comcon on 2007-06-07
> **Inxsible said:**
> If you are gonna keep Windows, you should boot into Windows and do a couple of defrags on the drive before you create partitions with GParted.


I had done one defrag before i get here with disk defragment.
I have to do more?
thanks

---

### Post by Inxsible on 2007-06-07
In that case, do the defrags and then check these links out for more information on partitioning and installing :
 
[Partitioning]("http://www.psychocats.net/ubuntu/partitioning")
 
[Installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Inxsible on 2007-06-07
> **Comcon said:**
> I had done one defrag before i get here with disk defragment.
I have to do more?
thanks
 
I would perform atleast 3 passes, but one should be good enough too if you didnt have too many fragmented files.

---

### Post by Comcon on 2007-06-07
i am almost done but why it tell me that it do not detect the used space?
thanks

---

### Post by Inxsible on 2007-06-07
Because you only have one partition of around 37GB. You need to shrink the partition, so that you will have some free space to install Ubuntu

---

### Post by Chethan N on 2007-06-07
If you want to dual boot Ubuntu with Windows its simple. If you have 160GB of HDD where in 120GB is being used by windows and rest 40 odd is left out, now if you wanna install Ubuntu in that space of 40GB odd only, then choose the option of " Guided - Use the largest amount of continuese disk space avaliable" while partitioning.  This option will make use of the 40GB odd disk  space avaliable for Ubuntu OS.  If you choose the first option avaliable during partitioning, Ubuntu will take away half of the free disk space avaliable on drive C in windows. So Ubuntu will add those space taken away form windows and adds upthat to 40GB of free space.  unless you want the manually edit the size for Ubuntu's directory or setup some kind of logical drive on Ubuntu , I would suggest you to select the third option during partitioning which will not Interfere with your windows installation.:D

---

