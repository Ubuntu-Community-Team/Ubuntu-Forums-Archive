---
title: "Trying to install Ubuntu"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by qw3rty3 on 2007-12-18
I used Ubuntu a year ago when it was the only OS on an old computer.  I'm trying to install it now but am having problems.

I'm using a hard disk with 2 existing partitions.  The first is a OS X partition, the second is a Windows XP partition.  I want to install Ubuntu on a third partition..

This is what I do:

Startup with the install disk.  

Choose "start Ubuntu in safe graphics mode"  (the first "Start or Install Ubuntu" gives me a garbled screen)

Open "Install"

Click "Forward" a few times

At "Prepare disk space" I choose "Manual"

I create a partition and click "Forward"

I get this message:
"No root file system
No root file system is defined
Please correct this from the partitioning menu"

Thanks in advance for any help

---

### Post by JillSwift on 2007-12-18
Edit the new partition and give it a mount point of "/". (No quotes)

---

### Post by qw3rty3 on 2007-12-18
Thanks for repling so fast.  
One more question.  What size should my swap space be?  I have 4 GB of RAM.

---

### Post by Lord DarkPat on 2007-12-18
it's always best to have 1 gb of swap :):popcorn:

---

### Post by hyper_ch on 2007-12-18
and you know that you can only have 4 primary partitions? If you require more, you'll need to make use of extended/logical partitions.

---

### Post by qw3rty3 on 2007-12-18
> **Lord DarkPat said:**
> it's always best to have 1 gb of swap :):popcorn:

Is it better to have 2 or 4 gig?  I have a 500 gig HD and want to do this right.

---

### Post by the Didey on 2007-12-18
I'm pretty new myself.

Everyone seems to have a different opinion on this from:

BAH, you don't need it! 500MB
to 
2 times your RAM.

I've never seen anyone suggest more than 2GB though. and with all that space you could probably spare it. 

have fun.

---

### Post by hyper_ch on 2007-12-18
You only need at least equal your ram if you are on a notebook and to suspend to ram (or hibernation). Then you should have swap at least equal your ram.

But as you have 4 GB of ram, I wouldn't get any more swap.

---

### Post by Paqman on 2007-12-18
With 4GB of RAM you probably won't ever touch swap space. 1GB should be plenty.

Incidentally, have you considered creating a seperate /home partition while you're at it? It'll allow you to retain all your software config files and personal settings if you ever reinstall or switch distros. That's really handy for upgrading, for example.

---

