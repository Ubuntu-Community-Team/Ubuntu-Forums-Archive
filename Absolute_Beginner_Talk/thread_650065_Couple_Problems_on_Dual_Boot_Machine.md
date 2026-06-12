---
title: "Couple Problems on Dual Boot Machine"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Shibby73 on 2007-12-25
Hello  Happy Holidays.

OK so I installed Ubuntu Studio on a computer at my parent's house a few months ago.  It was working fine, dual booting into Ubuntu Studio with one problem... it doesn't like to automatically connect to the internet (they use a USB wireless device).  

1) Ubuntu Studio - Not connecting to the internet via USB wireless device.

Bigger problem for my parents now is:
They had a bunch of power surges this past week.
NOW... they can not boot into WIN XP Multimedia (dual boot does get us into Ubuntu Studio - which is the first GRUB default if they start the computer unattended).  We can get into Ubuntu studio but have no internet connectivity... I even reset their wireless router which did not solve that problem.

2) When selecting WIN XP get the option to go to last known working version and that crashes so does the Normal Mode.
What they get is the computer sometimes showing WINDOWS XP logo but then it crashes back to shutting off the computer and restarting.

Any ideas or suggestions?
I was hoping to connect to the internet in Ubuntu Studio and trying to find a fix for the WIN XP side?  But I am fairly dumb when it comes to all this now.  My family now has a computer that can't do anything like get to the internet in either system and they want to run WIN XP programs.

Anyone else have similar problems after power surges?

Thank you.

-shibby73

---

### Post by Dakine858 on 2007-12-26
**if your wireless lan did not start when you booted up Ubuntu, open a terminal and type " sudo iwconfig wlan0 " without quotes. wlan0 represents the name of your network adapter and wlan0 is a fairly common assignment from linux when setting up a new adapter. as far as not being able to boot into xp, do you have ubuntu and xp installed on different partitions of the SAME hard drive or do you have 2 separate hard drives with xp on one and linux on the second? Before you reply to that question, start your computer and boot into the BIOS. most machines use the "del" key, F11 or F1 to get into the BIOS. Once you hit the "on" button, repeatedly hit the "F1" key (or respective key to your machine) and the BIOS will pop up. use right arrow key to navigate over to the "Boot" section and tell it which hard drive/partition to boot first and select the one with xp installed on it so you can restore your boot files to bring back your previous working dual boot setup.**

Lastly, purchase a high quality surge protector to plug your computer into and or a backup powersupply (if surges happen a lot) to prevent these conflicts in the future.

---

### Post by ShaNana on 2008-01-01
Thank you.  This is Shibby73's mom.  


Contacted Sony and got a restore CD images disk - cost me $17.95 plus tax and shipping.  Of course the computer was over 1 year old so I also had to pay for phone support since none of this was available online.

My son restored the entire hard drive using their CDs, setting the hard drive back to factory settings (erasing all  partitions).  

He wants to try to clone the drive image and used a Ubuntu 7.1 live CD to run a program called Gparted? and created 4 partitions on the hard drive, sda1 and sda2, formatted as NTFS (each @ 58 GB) and sda3 and sda4 which are eta3 (each @58 GB). 

He's trying to learn how to use Clonezilla and System Rescue CD in order to copy any drive images to CD/DVD/external HDD.  Apparently the instructions are very  long and have all possible scenarios.  

Any help would be appreciated to avoid how to do this in the future.

---

