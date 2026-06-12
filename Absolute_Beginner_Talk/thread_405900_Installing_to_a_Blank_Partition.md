---
title: "Installing to a Blank Partition"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by JerryAtrik on 2007-04-10
hi , I am reading the official Ubuntu book and I have looked through the forum .My Quearry is ,I have Windows XP installed and have a blank partition which I have formatted from NTFS to Fat32 . Is it best to divide the blank partition into three ie: (1 ) for Ubuntu ( 2 ) for the Swapfile (3 ) for my Ubuntu work folders .OR is it best to just let the installation sort it out for itself ? 

I dont want to loose WIN XP until I am reasonable proficient with Ubuntu.

Your help/input would be greately appreciated

cheers Jerry

---

### Post by Obor on 2007-04-10
Some people prefer 
1. / (root)
2. /home
3. swap

I use the same partition for root and home (which are ext3) and a separate windows share partition (fat32).
You can create and format all the partitions during the install if you choose the option to manually edit partition table. 

Few ideas about how to split your partitions here [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by finferflu on 2007-04-10
> **Obor said:**
> Some people prefer 
1. / (root)
2. /home
3. swap

I use the same partition for root and home (which are ext3) and a separate windows share partition (fat32).
You can create and format all the partitions during the install if you choose the option to manually edit partition table. 

Few ideas about how to split your partitions here [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
I second that. Having a separate /home partition is very handy.

---

### Post by JerryAtrik on 2007-04-10
Many thanks to Obor and finferflu , your advice is great as is the Psychocats explanation .If I get it wrong now I deserve to be shot.
cheers Jerry

---

