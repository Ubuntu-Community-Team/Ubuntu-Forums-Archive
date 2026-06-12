---
title: "Please help, installing ubuntu dual boot"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by ale2283 on 2007-11-12
Hi,  im a new user, please I need some help
I tried to install ubuntu dual boot in a couple ways but none of them worked for me 
I have a DELL XPS 600
Chipset 	nVIDIA nForce4 SLI X16 Intel Edition
Pentium dual core 830  3ghz
2048 MB  (DDR2-667 DDR2 SDRAM)
Graphic  card 	NVIDIA GeForce 6800  (256 MB)
Hard drive 	NVIDIA  STRIPE   298.02G  (298 GB)  Raid 0   (2  x 160 gb drives )
This is the problem :
I used live cd to install ubuntu, on the screen where I have to decide the partition I want to use just appears the  2  160 gb hard drives  (I have a  70 gb NTFD partition that I made with partition magic).
I tried different types of partitions as the ubuntu manual indicates but none of them worked.

Also I tried to install it with wubi but after the installation, when I restart the pc and choose ubuntu it appears a black screen that says :  CANT ACCES TTY; JOB CONTROL TURNED OFF.
Please if someone can help me, I really want to install ubunu without erasing windows.

---

### Post by DutyDuty on 2007-11-12
The Live CD should make a partition for you. I'm not proficient with your problem, but did you stop the install or did it fail?

---

### Post by ale2283 on 2007-11-13
Nop, doesn’t  recognizes my partitions, and the hard drive has a raid 0, so if I install in one of the 2 hard drives windows will probably be erased   
I stopped the install becouse i need to use XP

---

### Post by Shinbu-Otaku on 2007-11-13
although im pretty certain Ubuntu can use RAID drives, maybe there is a compatability issue with your RAID drive...

i have yet to have a problem installing, both on an IDE and SATA drives, so im not 100% sure, but it is a possibilty. If possible, try to install it on a spare IDE/SATA drive (if you have one) and see if thts the problem. You could also dual boot it that way, but it may require you buying a new hard drive/cables etc

sorry i cant be of much more help

---

### Post by mcduck on 2007-11-13
> **ale2283 said:**
> 
I used live cd to install ubuntu, on the screen where I have to decide the partition I want to use just appears the  2  160 gb hard drives  (I have a  70 gb NTFD partition that I made with partition magic).
I

Ubuntu cannot be installed on NTFS partitions. It's a Microsoft's proprietary file system that isn't able to store Linux/Unix-style file permissions.

The easiest way is to just remove the partition you have made, and leave some empty, unpartitioned space on the disk. Ubuntu's installer will recognize that space and create the needed partitions for you.

---

### Post by jryprt on 2007-11-13
> **ale2283 said:**
> Hi,  im a new user, please I need some help
I tried to install ubuntu dual boot in a couple ways but none of them worked for me 
I have a DELL XPS 600
Chipset 	nVIDIA nForce4 SLI X16 Intel Edition
Pentium dual core 830  3ghz
2048 MB  (DDR2-667 DDR2 SDRAM)
Graphic  card 	NVIDIA GeForce 6800  (256 MB)
Hard drive 	NVIDIA  STRIPE   298.02G  (298 GB)  Raid 0   (2  x 160 gb drives )
This is the problem :
I used live cd to install ubuntu, on the screen where I have to decide the partition I want to use just appears the  2  160 gb hard drives  (I have a  70 gb NTFD partition that I made with partition magic).
I tried different types of partitions as the ubuntu manual indicates but none of them worked.


Also I tried to install it with wubi but after the installation, when I restart the pc and choose ubuntu it appears a black screen that says :  CANT ACCES TTY; JOB CONTROL TURNED OFF.
Please if someone can help me, I really want to install ubunu without erasing windows.


1st backup your data , files  then make sure you backed it up & defrag. your hard drive 2 or 3 times 

 Use your Partition Magic in XP and  made  XP partition smaller reboot with live CD  when you get to the  partitioning
part  used guided with largest unallocated space it will leave XP .

---

### Post by ntu on 2007-11-13
Here is a method I have used for dual booting 2 hdds:
[http://www.pperry.f2s.com/linux-dualboot-2hd.htm](http://www.pperry.f2s.com/linux-dualboot-2hd.htm)

Alternatively if you wish to be extra cautious, you could remove the hdd with Windows on it and install Ubuntu on the other hdd, then put Windows hdd back in making sure it is the master and Ubuntu hdd the slave. Then you dual boot by going into the bios of the computer.

---

### Post by ale2283 on 2007-11-13
thanks guys for your help ill try that and then asnwer back

---

### Post by ale2283 on 2007-11-13
Ok I tried all the options that were posted here and none of them worked for me, ubuntu doesnt show any partitions.
does enyone knows the problem with WUBI??

---

### Post by Amstell on 2007-11-13
What happened when you made free space in pmagic and then tried to install ubuntu?  Did it recognize it or what?  That would be my main suggestion just as duck said.

---

### Post by white_sox_fan_82 on 2007-11-13
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3")

Try this.  These are the same steps I used and it worked great.  Very easy to do, just make sure all your Windows files are backed up...

---

### Post by ale2283 on 2007-11-14
ok thanks.
Nop After i partitioned de disk with partition magic doesnt recognices the partitions i made.

---

