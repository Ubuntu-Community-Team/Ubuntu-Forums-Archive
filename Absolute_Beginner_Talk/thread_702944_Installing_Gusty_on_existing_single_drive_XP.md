---
title: "Installing Gusty on existing single drive XP"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by universalis13 on 2008-02-20
New to Linux as well as xp. Have xp system already running with an unused 18gb partition. Would like to use this empty 18gb backup partition to install gusty. I have my xp system backed up on CD-RW disks just in case. Is it possible to setup a Linux partition using this 18gb of unused space without effecting existing xp syste?

Thanks

---

### Post by internetishere on 2008-02-20
It should be i have vista and ubuntu gutsy when i first installed it had to go through a couple process to get my files on my vista back up and running as long as you have a recovery drive you should be fine but if you dont have a recovery drive im not sure

---

### Post by universalis13 on 2008-02-20
Thanks

Can you point me in the right direction for instructions on setting up this xp partition to run Gusty.

Thanks

---

### Post by jcitguy78 on 2008-02-20
you need to use G Parted for the partition, do you have the Live CD with ISO?

---

### Post by ace007 on 2008-02-20
The process is really simple.  All you need to do is: (ALL THIS IS ASSUMING YOUR 18GB PARTITION IS EMPTY OR YOU DONT MIND LOSING ANYTHING ON IT, THE OTHER PARTITIONS WITH WINDOWS WILL BE UNAFFECTED)
1). Download Gutsy and Burn on Slowest Speed to ensure quality

2). Boot from Gutsy Live CD

2b). Putz around the Live CD to make sure everything you like to do normally works and there aren't any obvious problems with your computer running gutsy.

3.) Assuming the 18GB partition is NTFS, you will have to delete it and reformat it to ext3. This is done by going to System>Admin>Partition Editor while running the Live CD.  Select the partition and delete it. 
3a). First create a partition for the Linux Swap file.  This should be approx the size of your RAM or about 1 GB is plenty.  

3b). From the existing raw space create an ext3 partition.

4). Choose the install icon from the desktop and follow the instructions [COLOR="Red"]**PAY ATTENTION TO STEP 4**[/COLOR]. You want to choose the ext3 partition you just created, not use the entire disk.  

5.) Enjoy your sweet freedom from all things M$

Welcome to Linux!

---

### Post by universalis13 on 2008-02-20
Yes I have gusty live CD. Matter of fact I posting from it now.

I will give your ext3 instruction a try.

Thanks

---

### Post by universalis13 on 2008-02-20
OK. I've deleted my 18gb XP ntfs "D:" drive or, more accurately, partition. Graphically it seems to make sense. Now I have the "Create new partition" dialog opened. 

First off, do I "Create as:" Primary Partition or Extended Partition. I have "linux-swap" selected for my Filesystem.

Secondly, what do I set my "Free Space Preceding" and my "Free Space Following" to?

Thanks

---

