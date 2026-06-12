---
title: "Install Dual Boot"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by share666 on 2007-11-10
OK -- I am sorry to ask these questions but I have never used Ubuntu.

I have two drives with XP installed on the first one.  My second drive has been partitioned and I have an empty partition I would like to install 7.10 to.  I was hoping to be able to set up a dual boot.  The problem I have is that when I am installing (from a cd) the "partitioner" pops up and asks me about mount points (I am in manual mode - not automatic) I have no idea what to do.    Should I not be using manual mode and go with automatic?  Will that wipe out my XP drive?  I am sure there is a simple explnation for all of thiis but I can't seem to find exactly my issue in amongst the hundreds of posts.

---

### Post by overdrank on 2007-11-10
> **share666 said:**
> OK -- I am sorry to ask these questions but I have never used Ubuntu.

I have two drives with XP installed on the first one.  My second drive has been partitioned and I have an empty partition I would like to install 7.10 to.  I was hoping to be able to set up a dual boot.  The problem I have is that when I am installing (from a cd) the "partitioner" pops up and asks me about mount points (I am in manual mode - not automatic) I have no idea what to do.    Should I not be using manual mode and go with automatic?  Will that wipe out my XP drive?  I am sure there is a simple explnation for all of thiis but I can't seem to find exactly my issue in amongst the hundreds of posts.

Hi and welcome, you will need a" / "root partition, and a swap. the swap is usually twice the amount of memory up to 2gigs. 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Good luck!
Edit if you like you can set up a home partition also. Forgot sorry :)

---

### Post by oilchangeguy on 2007-11-10
> **overdrank said:**
> Hi and welcome, you will need a" / "root partition, and a swap. the swap is usually twice the amount of memory up to 2gigs. 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Good luck!
Edit if you like you can set up a home partition also. Forgot sorry :)

sorry i've got to disagree with you on this one. there's no way any computer needs 2gb of swap/virtual ram. if it does it's got major problems.  if the computer has more than 1gb of physical ram, you could in theory have no swap space. physical ram is much faster than virtual ram. setting up this much swap is a waste of hard drive space. anybody out there who questions this, go to system, admin, and system monitor. and see how much swap/virtual ram your computer is NOT using.

---

### Post by overdrank on 2007-11-10
> **oilchangeguy said:**
> sorry i've got to disagree with you on this one. there's no way any computer needs 2gb of swap/virtual ram. if it does it's got major problems.  if the computer has more than 1gb of physical ram, you could in theory have no swap space. physical ram is much faster than virtual ram. setting up this much swap is a waste of hard drive space. anybody out there who questions this, go to system, admin, and system monitor. and see how much swap/virtual ram your computer is NOT using.

Hi and no problem you are correct, I just stated that wrongly, I did not know how much memory the op has and I should had specified that correctly. I have 1 gig of memory and my system never uses the swap. :)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by hernaaan on 2007-11-10
I recommend installing from a Live CD (Ubuntu Desktop), which means graphical mode, not text. If you have Ubuntu (Gnome), you will find no problems setting up things. When it comes to partitions, select *Use the biggest free space...* (I don't know exactly because I speak spanish). The point is to select the one that mentions Ubuntu will be installed on free space, and not over the whole disk or resizing another partition.

The installer will automatically create the ext3 and swap partitions with an appropiate size. In my case, the swap got nearly 700 MB.

If you have downloaded the Alternate CD, you aren't supposed to have problems, either. Just search for *Guided partitioning*, and select *Free space*, or something.

The mount points are the logical drives that are mounted (you can access them) once you start Ubuntu. They are located in /etc/fstab (text file).

Hope it helps you.

---

### Post by louieb on 2007-11-10
> **share666 said:**
> OK... the "partitioner" pops up and asks me about mount points (I am in manual mode - not automatic) I have no idea what to do.    Should I not be using manual mode and go with automatic? 

Setting up dual boot the 1st time is kinda scary. Go with the manual never know what your going to get with the automatic.   You should have an install partition minimum size 5 gig, more is better and a swap partition too 1/2 gig is fine.  
How did you create the partition?  On the LIve CD  go to system>admin>partition editor. Find the partition you want to use and remember its **/dev/sd@# **your going to use it for your / (root) partition when the installer asks for the mount point. While your there see if you can shrink it by a 1/2 gig or so and create a swap partition too .

IF you have problems creating a swap partition. The post a shot of the gparted window (Alt+Print Screen). Partition layout has rules   as to # and type of partitons on a drive. 

Once you have your partitions created and you know there Linux names then your all set to use the manual partitioning option of the install.
Good luck.

---

