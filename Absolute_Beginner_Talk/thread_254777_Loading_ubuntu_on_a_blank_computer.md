---
title: "Loading ubuntu on a blank computer"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by oldglide on 2006-09-10
I'm new to this so bear with me. I am intending to load ubuntu, latest version, to a totally blank HDD and computer. Will this cause any problems? Will I still have to partion the HDD? If so, what would be the best way? I'm really looking forward to this.

---

### Post by tkjacobsen on 2006-09-10
The ubuntu installer features a great partitioner, if you don't have specific needs, you can just go on with the default settings.

---

### Post by jorn on 2006-09-10
Try out the live-cd to see if all the hardware is supported.

---

### Post by Najand on 2006-09-10
Partitioning is a need, becuase you need at least 256 MB of Swap Partition. However UBUNUTU like other major distros has the ability of partitioning the disk during installation. If you are not planning to install any other OSes on your computer, start the installation process by loading Ubuntu Live CD and clicking on the INSTALL on your desktop. At Partitioning Level, select Auto-partitioning and everything will be done automatically for you.

---

### Post by bobbybobington on 2006-09-10
if you are going to put windows on it as well, make sure you install it first. This is because if you install second windows it will install its own boot loader over ubuntus, so getting to ubuntu will be difficult. On the other hand, if your not installing windows... more power to you:-D

---

### Post by arkangel on 2006-09-10
I  always do this in all computer i install linux:
1. the first partition  I use for root (hd1)in my case 50 gb out of 100gb 
2. (I read many times ,it is not a must but  seems to be a common advice  ) a good size for the swap is to double the ram (2 gb in my case )
3. then i have a 3rd partition hd5 for my home , the rest ,  when installing it will ask if you want to mount this partiton and where , so   hd5 goes to /home,  if something happens  in your os, if you reinstall or something else  your data will be always secure in its  own partition

---

