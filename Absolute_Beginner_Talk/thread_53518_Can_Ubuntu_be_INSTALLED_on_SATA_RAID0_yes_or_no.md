---
title: "Can Ubuntu be INSTALLED on SATA RAID0? yes or no?"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by snoochems on 2005-08-01
Hi all.
I'm new to linux.  
I decided that i might take my first step and investigate this alternative to windows.

But, i only have 2 HDD's, and they're in a stripped array.  I'm have no intentions what so ever to take them out of the array.  

So, if Ubuntu can not be installed on a RAID0 drive, then i will not bother proceeding.

SO, CAN UBUNTU BE INSTALLED ON A SATA RAID0 DRIVE?

Yes - awesome, then that's that.  I'm in.  Is it a simple process?

No - well, what linux distro's are there that can be installed?



Additional info:
System:
AMD64 3200+
Abit AV8 mobo
1 GB RAM
2x WD SATA 120GB 8MB cache HDD in stripped array
VIA 8327 RAID controller.
Will also want to run Windows XP x64 in dual boot.
Require RAID0 for my video editing i do.

---

### Post by JuanPedro on 2005-08-07
I AM EXACTLY IN THE SAME CASE

Same chipset and same requirements.. for a Studio for Audio Recording.

---

### Post by Gav-UK on 2005-08-08
Im number 3.

I have 2x 80g drives in a raid formation. At present i have 130g set aside for my windows partition and i have 30g left which i want to install Kubuntu onto.

As with everyone else the partitioner only sees the two drives not a single raid setup.

---

### Post by synap on 2005-08-08
I did a software raid0 with the installer with little problems.

This is for a clean install, there are some how to's around that can help with moving to a raid.


I’m going off the top of my head so this may not be totally accurate but should point you to the right direction.

In the installer manually set the partitions.

On your first disk (sda) set a small partition for /boot at the beginning of the disk.

Calculate what your swap partition should be and divide that by the # of drives (I read that a swap raid is faster, since it spans across all the disks).

Then create a raid auto detect partition for both primary and swap on each drive.

Select the create raid option and create your Multidisk raid, and create one for primary and one for swap.

Select the raids drives and configure them as so.


For some reason when I did this the swap didn’t take, I was messing around with it a bit so it could have been something I did during the install.  The system still booted however and I just manually created the swap raid.

Example:
mdadm --create /dev/md1 --level=0 --raid-devices=4 /dev/sda3 /dev/sd[b-d]2  
(again going off the top of my head) man or google mdadm for help.

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=snoochems]
SO, CAN UBUNTU BE INSTALLED ON A SATA RAID0 DRIVE?
[/QUOTE]


Can it? Yes. Can it install using every RAID controller card in existence? NO.

[http://www.ubuntuforums.org/showpost.php?p=292227&postcount=4](http://www.ubuntuforums.org/showpost.php?p=292227&postcount=4)

---

### Post by Larkki on 2005-08-09
You guys might want to check out this post before you start to install. It has pretty detailed instructions on how to use software raid for ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=55211](http://www.ubuntuforums.org/showthread.php?t=55211)

---

### Post by JuanPedro on 2005-08-09
so snoochems we are fucked up until some distro supports our RAID controllers that IMO are very common, used by a lot of people, and should be supported..

Just a thought.. Lots of servers run linux over the world.. SERIOUS Servers use Raid arrays. Shouldn't Linux be more friendly with Raid Arrays?

I'm not saying that one cannot buy another drive and install linux on it, outside the array.. i was just wondering that Linux is SO good for some things.. and SO bad for others..

Hope linux distros fix this (if it hasn't been fixed yet), because i like linux... but it could be a lot more..


Just think about this (in this context).. while linux is fighting to get a good sofware raid aray working, Windows suports Both, software and hardware Raid Arrays, with absolutely no problems at all.


Well if someone can help us with this, would be perfect, because i have to do A LOT of programming in Linux.

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=JuanPedro]so snoochems we are fucked up until some distro supports our RAID controllers that IMO are very common, used by a lot of people, and should be supported.[/QUOTE]

Linux (as in the kernel) only supports RAID hardware that has open specs. Thats all that matters.

Popularity doesn't matter. That Windows can do it doesn't matter. That its good hardware doesn't matter. That Ubuntu should support it doesn't matter.

All that matters is if the hardware maker is friendly to Linux. If they are not, there is nothing Ubuntu or any version of Linux can do. That is the truth. Its not our fault that some companies refuse to work with us....we are doing the best we can.

Linux is really good with some hardware and really bad with other hardware because some hardware companies are really good about supporting Linux and others are not. Case closed.

---

### Post by snoochems on 2005-08-10
Well, i've kind of given up on trying up the idea of installing linux on my 'good' computer.

I was going to throw in an extra HDD just for linux, but i CBF'd.  I installed ubuntu on my laptop instead.

My 'good' computer can say with Windows x64 for now.

---

