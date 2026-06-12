---
title: "Problems after installing ubuntu 7.04"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by magnity on 2007-04-30
Hi,
I want to start by saying that I am new to the Ubuntu scene (noob). I installed Ubuntu 7.04 after installing Vista Home Premium on my machine ( Dell XPS M1210 ). 
Just to give an idea, I have 120GB HDD and I installed windows vista then I installed Ubuntu. During the installation I assigned 11GB for Ubuntu; after dabbling with Ubuntu for a few hours I rebooted and I found that the windows partition has became 10.3GB. So basically I lost about 100GB.

It is very strange since I did not input the value 10.3GB anywhere after the installation Ubuntu. And I did test vista after i installed it, and it did show the entire 120GB before installing Ubuntu.

I hope some of you guru's can help a noobie like myself in solving this problem.

Mag.

---

### Post by akudewan on 2007-04-30
Try running a program such as "gparted" to see whats up. You can also run ```
sudo fdisk -l 
``` in a terminal.

---

### Post by Spike-X on 2007-04-30
It sounds like the installer has changed everything that's not Windows on your HD to free space. Then it's made an 11Gb partition like you told it to, and left the rest as free space. You'll just need to put a partition onto the free space to be able to use it again.

---

### Post by Nythain on 2007-04-30
or use a program like gparted or partition magic to resize the windows partition back to what it was... if that is the problem

---

### Post by Spike-X on 2007-04-30
Would it be possible to add the freed space back onto the Windows partition with Ubuntu installed smack bang in the middle like that? Or would he need to make it a separate partition?

---

### Post by Nythain on 2007-04-30
thats a good question... im not the most familiar with how the different filesystems handle the resizing of partitions and how they write thier partition tables and whatnot... you might have a good point and they might have to just turn the free space into a new partition and set it up as a storage area... or just nuke ubuntu, resize the partition in windows, and then reinstall ubuntu being carefull of the choices they make during the partion setup part

---

### Post by akudewan on 2007-04-30
> **Spike-X said:**
> Would it be possible to add the freed space back onto the Windows partition with Ubuntu installed smack bang in the middle like that? Or would he need to make it a separate partition?

You can add the space to the windows partition using gparted

---

### Post by magnity on 2007-04-30
thanks a lot guys. I will try what you suggested and I will let you know if it works or not.

Mag

---

### Post by croxi on 2007-04-30
I had major problems setting up my partition with UBUNTU, I wanted to make it so I could dual boot  with WINXP and UBUNTU 7.06 and the partition wouldn't work. In the end it just made me get rid of XP and that left me with just UBUNTU on my laptop. 

Its fortunate that I have 6 other PCs to play with using XP and UE Vista.

---

