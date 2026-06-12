---
title: "Refusing to Partition"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by buddhalover on 2006-07-22
Gparted won't partition my HD. 
I tried manual partition but it gets me an error message.
I'm using an Ubuntu liveCD that I disc checked and slowburned.
It's not the CD...
I don't know what to do to install.
I've been trying for days. 
So frustrating.

---

### Post by Jagot on 2006-07-23
If you're dealing with a Windows partition there in terms of trying to resize it to fit Ubuntu on then you may want to try defragmenting the partition a couple of times first.

---

### Post by buddhalover on 2006-07-23
I just defragmented once. I'll do it twice.
Thanks for the help.

---

### Post by Jagot on 2006-07-23
If it still persists after that can you tell us what the error message is that you get.

---

### Post by buddhalover on 2006-07-23
Error resizing/move 
after defragmenting
it still persists

---

### Post by OU812 on 2006-07-23
Before installing linux on windows:

1. Defrag - Done.
2. Run scan disk - Please do this. 

Then try to partition. 

Note: You must unmount the partition before you can work with it. Unmounting a partition can sometimes take quite awhile.

john

---

### Post by buddhalover on 2006-07-23
Defrag check
Scan disk check
will try partitioning again...

---

### Post by buddhalover on 2006-07-23
ok it still doesn't work](*,)

---

### Post by buddhalover on 2006-07-23
why can't it resize the partition?
arggg ](*,)

---

### Post by buddhalover on 2006-07-23
its still the same error ](*,)

---

### Post by buddhalover on 2006-07-23
anyone feel like helping?

---

### Post by navymom on 2006-07-23
buddhalover, does it tell you anything like the hard drive you're trying to partition has at least one error or bad sector?  that's what mine told me when i tried to install it last night....so, i'm just holding off and waiting for staples to open. :P

---

### Post by _simon_ on 2006-07-23
Are you trying to manually partion or using automatic?

---

### Post by buddhalover on 2006-07-23
when i try automatic...
it claims i don't have enough space... which i do...
when i try manual..
it gives me an error message indicating that it cannot resize the main partition...

---

### Post by buddhalover on 2006-07-23
navymom, i defragged three times and disk checked twice...
it doesn't indicate bad sectors on the partition.

---

### Post by navymom on 2006-07-23
k i don't know if this will help or not but i found this article on doing dual boot installs....i'm trying to anticipate every problem i might have when my husband eventually gets home with my new hard drive so i can start my own install. :P  at any rate, i would quit trying to partition using the livecd and follow these instructions...apparently there is a problem with the XP NTFS partitions...this article may help you if that's the problem.

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by Omnios on 2006-07-23
I had better success with Qtparted with the ntfs blug in. First off I tryed qparted a long time ago withut success. I found Qtparted worked much better at resizing and making partitions. First off what I did was shrink the ntfs partition and used windows XP to make the partition which was to be a Vfat32 partition for my WinXP My Documents drive which was also  shared with linux as Documents. I used the Xp disk manager to enshure capability with Xp as a partition though you probably can use Qtparted also though I have heard a few stories where the partition had trouble in windows. ALso I used the Linux command line to make a vfat32 format wich does a pretty good with parmitions in linux. 

 Another note you can shrink a drive to the left and possibly even move an empty partition but not to the right from what I have heard.

---

### Post by confused57 on 2006-07-23
If Omnios suggestion doesn't work, your might want to try disk drake:

[http://www.ubuntuforums.org/showthread.php?t=114142&highlight=pclinuxos](http://www.ubuntuforums.org/showthread.php?t=114142&highlight=pclinuxos)

---

### Post by moshuptrail on 2006-07-23
You may have bad blocks.  GParted just kind of quits if the partition has even one bad block.  I had to use ntfsresize and fdisk to partition the 20G HD on my Dell C610 laptop.  It is risky.  Evidently if the bad block lands in the wrong place very bad things can happen.  I was lucky.  Didn't care though - who needs a 10G partition of XP anyway?  (XP is sucking up the better part of 7G)

---

### Post by catlett on 2006-07-23
You should check you disk for errors. Gparted and most Linux partitoners will quit before committing a possible error. They don't give an output, they will just not perform the operation. That leads to the question, "what is the  issue?" Sometimes it is a non-defraged disk and there are files all over the hard drive. Sometime it is a bad sector and it doesn't want to move the bad sector.
So you should first run check disk in windows,
Boot into XP and go to Start<Run
In the run box enter ```
cmd
``` Then press enter. Now put in ```
chkdsk volume:/r
``` The /r option will run it to repair errors, locate bad sectors and recover readable information.
When you press enter it will prompt you with something like "the volume is in use, schedule chkdsk for next restart?" Type```
 Y
``` Then reboot and let windows run the disk check.
If that is fine then I would first suggest Partition Magic but if you don't want to pay the money, I use gparted live. It is the gparted you have been using but it runs of of a live cd like the ubuntu installer.
I have had nothing but good experiences with it. It is a small download, only 30mb and it is the only thing running on the live cd. There isn't an entire x window system that has to be run just to get at the partitioner.[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by OU812 on 2006-07-23
OK. It's been awhile since I've used gparted. But defragging and running scandisk were important steps. I googled a bit. Please read this (if you haven't already):

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

john

---

### Post by buddhalover on 2006-07-24
thanks for all the help people. i still haven't partitioned it properly for an ubuntu install. i have yet to try the suggested partitioning tools. but i've been playing around with the idea of deleting windows altogether....
do you think the cd will install if i go with option 2. (option 2 in live-cd install)
?

---

### Post by buddhalover on 2006-07-24
catlett, just tried the gpartition live cd.
it gave me an error message and claims that there are at least 4 bad sectors in the hdd. 
i tried defragmenting several times and also discheck. but same error.

---

### Post by buddhalover on 2006-07-24
chkdsk doesn't see the errors
defrag sees some unmovable files
gpartition detects errors still
how do i fix the errors?

---

### Post by buddhalover on 2006-07-24
is there a dskchk that works better than the one from windows? 
it can't find the errors that Gparted finds.

---

### Post by catlett on 2006-07-24
The way to deal with bad sectors is to reformat the whole drive. If it isn't physically damaged, then the format will return it to good. If it is physical, then it will remain bad.
Your drive can live with bad sectors. It can be a sign that the drive is nearing the end of it's lifespan or you can get lucky and it keeps on going.
I would suggest backing up your important data. Reformat the drive. Use the tools from your hard drive maker to do a low level format. I guess you could reformat with gparted but the utilities from your hd maker are free and created to work with your drive. I would try them first. I don't know what drive you have. Here are a few links to some popular drives.
Hitachi [http://www.hgst.com/hdd/support/download.htm](http://www.hgst.com/hdd/support/download.htm)
Seagate [http://www.seagate.com/support/disc/utils.html](http://www.seagate.com/support/disc/utils.html)
Maxtor [http://www.maxtor.com/portal/site/Maxtor/menuitem.8db0c3d6932ced37294198b091346068/?channelpath=/en_us/Support/Software%20Downloads](http://www.maxtor.com/portal/site/Maxtor/menuitem.8db0c3d6932ced37294198b091346068/?channelpath=/en_us/Support/Software%20Downloads)
Fujitsu [http://www.fel.fujitsu.com/home/drivers.asp?L=en&CID=1](http://www.fel.fujitsu.com/home/drivers.asp?L=en&CID=1)
Western Digital [http://support.wdc.com/download/index.asp](http://support.wdc.com/download/index.asp)
After you backup and reformat, make all your partitions. Just remeber, you can only have 4 primary partitions. You can have many logical partitions but only 4 primary.
Make the first drive ntfs and primary for windows. Then make your linux partitions.
Install windows first and linux second. (Hopefrully it will go that easy)

---

### Post by buddhalover on 2006-07-25
Omnios,confused57,moshuptrail,catlett,OU812,Jagot,navymom

thanks for all the help.
i opted to just forget about dualboot
and jump straight into it.
the install went pretty smoothly
with the loss of the desire to hold onto windows.
i appreciate the assistance you've all generously provided
thank you all again. :D 

buddhalover

---

### Post by catlett on 2006-07-25
Wow, I didn't expect that answer. Good for you. Nothing ventured nothing gained as they say. 
You'll find you can do all you want in linux. I started with dual boot and little by little I figured out linux and found solutions and apps for my problems until I have gotten to the point that I don't go into my windows install at all.
This is a great guide.[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)  All you have to do is follow the steps in order and copy/paste the commands from the page to your terminal.(just in case you haven't gotten your flash, mp3's and such)

---

