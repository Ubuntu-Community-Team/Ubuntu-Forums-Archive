---
title: "not booting"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by sandnesspeats on 2007-06-20
hi everyone,
                   only just joined so great to be a part of all this,the thing is i downloaded ubuntu from computer active site ages ago,i have tried installing it and everything seemed to install but i don`t get the boot screen along with windows xp prof,sp2,
any help would be great.
i am an absolute novel at this never used it before,i am just fascinated by it.
best wishes
:D

---

### Post by amsterdam on 2007-06-20
Perhaps you could describe what is happening, and not happening in a bit more detail.

What version did you download? 
Did the live cd work?
It sounds like you may be dual booting? do you want to have the option to run either windows or linux?

---

### Post by AriciU on 2007-06-20
You probably want to dual boot XP and Ubuntu. I'd recommend sticking with the XP boot loader and not installing GRUB in the MBR of the XP disc.

Anyway. You will need a program called "bootpa26". You can get it from [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

First you will need to create some partitions for linux. Go in XP and open your partition maker program and create 3 parititons. One around 10gb or whatever you want but no less then 5GB. Set it as Linux EXT2 (or ext3 if you wish but i don't use that). Make the next one around 500-1000mb or so and set it as Linux EXT2. The third one make it around 500-2000mb and set it as Linux Swap.

Insert the Ubuntu Live CD and boot it. Chose install and after a while you will be asked about partitions. You will have 3 options -> Automaticly usee free hdd space / Use whole drive / Manual. Something like this anyway...

Chose Manual paritioning and you will see your drives. The 10GB first Linux EXT2 partition set it as "/". The second EXT2 partition (500-1000mb) set it as "/boot".  The swap partition is autoset by default i think but set it as swap if it's not.

You will have an Advanced option somewhere over there... look for it. It will ask you to select the hard drive where you want GRUB to be written. You should select the /boot partition for it. You will have to remember what the partition is called (/dev/hdb2 if the HDD is on IDE or /dev/sdb2 if it's on SATA). You can't enter /dev/sdb2 in the Advanced tab for GRUB... you must use (HD0,0), (HD1,1) etc. So... for /dev/hda1 the HDD is (HD0,0) for /dev/hda2 it is (HD0,1) for /dev/hda3 it is (HD0,2) for /dev/hdb1 it is (HD1,0) for /dev/hdb2 it is (HD1,1) for /dev/sda1 it is (HD2,0) etc... 

You have to write down the order in witch the hard drives appear when you turn on the computer. HD0 = Drive 1, HD1 = drive 2 and so on... HD0,0 = drive 1, partition 1; HD0,1 = drive 1, partition 2; HD1,0 = drive 2 partition 1; HD1,3 = drive 2, partition 2 and so on. I hope you understand what i'm trying to explain here :D

Install ubuntu and restart. You will not be able to boot like it's your case right now.

Go in WinXP and open the command prompt. Go to the folder where you downloaded "bootpa26". Unarchive it and enter "bootpart.exe" in the command prompt console. You will see a list with all your partitions with a number in front of each one. Look for your 500-1000MB Linux EXT2 partition and remember the number it has in front of it. Then enter "bootpart.exe <number> bootsect.lnx". This will create a file called bootsect.lnx obviously. Copy that file to your C:\ drive or your main windows drive where the MBR is. 

Now go to your C drive or main windows drive and edit boot.ini. Put the following line in it: "C:\bootsect.lnx="Ubuntu 7.04"

Save it, reeboot and you should see Ubuntu 7.04 added to the windows boot loader. Select it and if you chose the write partition then GRUB should appear and you can boot ubuntu.

---

