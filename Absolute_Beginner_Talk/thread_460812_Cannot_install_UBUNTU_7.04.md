---
title: "Cannot install UBUNTU 7.04"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ca.kushagra on 2007-06-01
I have a P4/40GB/256MB system running with XP. The hard disk has 4 ntfs partitions. I tried to install Ubuntu from the cd. The system booted from cd properly and i selected the default option of start or install ubuntu. I reached the winodw showing the option of install and examples. When i clicked on Install the system kept on processing but nothing happened. I have tried many times.

I feel there is some problem with partitions.

Can any one provide me a link to download a free partition manager and also if some one could help me out on this as i wish to keep a dual boot enabled system.

---

### Post by AtrejuT on 2007-06-01
There always is the gparted live cd available here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

however, gparted is also on the ubuntu livecd. just look for it in the system/administration menu.

these 4 partitions could indeed be a problem since you are not allowed to have more than 4 primary partitions.

EDIT: oh, and for the dual boot: Ubuntu should automatically recognize your windows upon installation and make an entry in the boot manager for it.

---

### Post by ca.kushagra on 2007-06-01
Only one is primary partition. And i have checked the cd for errors using the option provided by the first window it shows no errors...

---

### Post by DerArzt on 2007-06-01
ok, your first problem is most likely this: hard drives can only have 4 primary partions. if you need to keep all of the partitions, you should look into using an extended partition.
I don't know your particular reasoning to having 4 partitions, but if it were me, i would probably consolidate them all into one, or maybe 2 (system partition and storage partition), and go from there for ubuntu. as to a partitioner...ive always like using the gparted live cd. it a linux live cd that boots to gparted and lets you move/resize/delete/create/etc partitions (no worries, it is very straight forward and easy to use). i find it to be far more useful than windows programs like partitionmagic because those programs need at least one partition to be mounted, limiting certain operations., whereas gparted runs off a cd so no partitions are mounted. to get gparted go to:
[HTML]http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828[/HTML]
download and burn the image, then reboot, and there it is. 

A warning: be very careful when editing partitions, as very simple mistakes can make you lose lots of data. 

As to dual booting, it basically sets that up for you when installing ubuntu from the live cd.

**Guess im a bit late with this. Oh well.

---

### Post by nlbs on 2007-06-01
The live CD is too slow it takes 45 mins to open a window Download teh text based Installer
It takes just 15 mins to Install.

---

### Post by AtrejuT on 2007-06-01
That is rather strange.

So you could try using gparted to manually make some room for ubuntu to install to. You might want to create two partitions for ubuntu, one for the system and one as swap. (Even better would be a separate partition for home, but we don't want to overdo it just yet, just get the system running right...)
gparted should hopefully be able to resize your existing partitions to make room for this.

If all does not help you could try booting the alternate install CD.

---

### Post by 6star.org on 2007-06-01
Try to find it from download.com

---

### Post by ca.kushagra on 2007-06-01
> **nlbs said:**
> The live CD is too slow it takes 45 mins to open a window Download teh text based Installer
It takes just 15 mins to Install.


May be i only waited for half an hour..............

---

### Post by ca.kushagra on 2007-06-01
> **DerArzt said:**
> ok, your first problem is most likely this: hard drives can only have 4 primary partions. if you need to keep all of the partitions, you should look into using an extended partition.
I don't know your particular reasoning to having 4 partitions, but if it were me, i would probably consolidate them all into one, or maybe 2 (system partition and storage partition), and go from there for ubuntu. as to a partitioner...ive always like using the gparted live cd. it a linux live cd that boots to gparted and lets you move/resize/delete/create/etc partitions (no worries, it is very straight forward and easy to use). i find it to be far more useful than windows programs like partitionmagic because those programs need at least one partition to be mounted, limiting certain operations., whereas gparted runs off a cd so no partitions are mounted. to get gparted go to:
[HTML]http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828[/HTML]
download and burn the image, then reboot, and there it is. 

A warning: be very careful when editing partitions, as very simple mistakes can make you lose lots of data. 

As to dual booting, it basically sets that up for you when installing ubuntu from the live cd.

**Guess im a bit late with this. Oh well.


Please tell me what happens to the NTFS format of the partitions if i use gparted???? How to handle ntfs or FAT32 with it, without damaging the data?

---

### Post by Lucifiel on 2007-06-01
GParted will not corrupt your ntfs partitions but... as always, be careful and make sure the partition selected are the ones you want to delete.

---

### Post by steve-shinn on 2007-06-01
> **ca.kushagra said:**
> May be i only waited for half an hour..............


I notice that you only have  256mbyte of RAM .... the minimum recommendation for Feisty is 512mybte

---

### Post by Lucifiel on 2007-06-01
> **steve-shinn said:**
> I notice that you only have  256mbyte of RAM .... the minimum recommendation for Feisty is 512mybte

Good catch, dude!

i missed that one. :)

Hmmm... okay, to the threadstarter, you now have a few choices, all of which are lightweight and run very fast on your 256 mb ram:

- Xubuntu

This is a much more lightweight version of Ubuntu and will work for your memory size.

- Wolvix 
Wolvix is really speedy and you might want to give this one a shot instead. 

- Damn Small Linux

- Puppy Linux

---

### Post by zvacet on 2007-06-01
Alternate CD will do the job.

---

### Post by Lucifiel on 2007-06-01
> **zvacet said:**
> Alternate CD will do the job.

Oh, won't he have problems using Feisty with 256 mb of ram?

---

### Post by nlbs on 2007-06-01
> **nlbs said:**
> The live CD is too slow it takes 45 mins to open a window Download teh text based Installer
It takes just 15 mins to Install. The text based Installer can run on 256 MB RAM well.
Cause I've Installed it in that way. And I also couldn't Install from Live CD.
Go here
[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso]("http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso")
See it On
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate]("http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate")

---

