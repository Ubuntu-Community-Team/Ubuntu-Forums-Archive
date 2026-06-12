---
title: "Installation woes...sorry!"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Al_Vampyre on 2006-09-03
This is my first post, and can I just say that if the people here hadn't seemed so helpful when I was searching other peoples posts for an answer I would probably have given up by now, so a big pat on the back all round:D 

OK, a little background first, I am an experienced Windows user but have never dabbled with Linux before so as far as Linix terminology goes I am a complete n00b! My question may have been answered in another post but if it was I didn't understand the answer so please bear with me...

My setup is as follows;

Opteron 165 on an Asrock 939 Dual Sata with 2Gb DDR400 and an X1800XT, using onboard sound. I have 3 HDD installed, WD Raptor SATA contains my XP install (which I would prefer not to touch if I can). 2 IDE drives on Primary channel, the master is a 200Gb Sammy Spinpoint which contains all my music, downloads, iso's, etc. The Slave is a 120Gb Maxtor which I was using a data dump and temp file repository. The Master on the Secondary IDE channel is a Pioneer 107 DVD RW.

The idea was that I would like to try Ubuntu, if possible migrating most of the stuff I do to Linux versions and maintaining XP solely for the few apps that don't have Linux equivalents and for games.

So I downloaded the desktop cd and started playing and doing some reading up on my favorite apps to see which ones would work in Linux.

A couple of nights ago I decided to clear the drive that was easiest to clear (ie the IDE Primary Slave) and install Ubuntu as I was really impressed with the LiveCD.

Everything seems to go as planned, I get to choose all my options etc and on partitioning instruct the Live CD to clear hdb and use that for my Ubuntu install which it duly does, sets up the partitions correctly (as far as I can tell) and goes on to install the files. Installation reports as completed, I get the instruction to take out the disk and reboot, so I do.

On first attempt the PC boots straight into XP so I reboot and hit F11 which on my mobo brings up the boot disk options and I tell it to boot from the Maxtor where I have just installed Ubuntu. I then get an 'Error Loading Operating System' message and nothing else. Thinking something had fouled up somewhere I went through the install process again with exactly the same result.

I have searched for an answer in various forums and I get the impression that towards the end of the install process I should have been asked where to install Grub(?)and that it should be installed on the MBR of the SATA drive (cos thats where XP resides). Thing is I don't remember the installer even acknowledging that I had another OS installed but I'm fairly sure that it did see the SATA drive.

Any help would be greatly appreciated, as I really would like to minimize my Microshaft dependency! Thanks in anticipation...

Vamp

---

### Post by taurus on 2006-09-03
I have both IDE and SATA on my machine (except I have Gentoo & Ubuntu, no XP is allowed around here) and I can use GRUB (on MBR) to boot either.  So, I recommand you install GRUB on the MBR to boot either XP or Ubuntu.

---

### Post by Al_Vampyre on 2006-09-03
Wow...speedy response, thank you, I'll have a search about and find out how to install it. Don't quite understand why it didn't install on the two attempts from the live cd though, it should have if I'm reading correctly.

---

### Post by Al_Vampyre on 2006-09-03
OK, I've done some reading and I think that I should be installing GRUB on the MBR of the SATA drive (which has XP on it) which would be /dev/sda (?)and somehow telling it to boot Ubuntu from /dev/hdb1 (the maxtor ide slave). Is this correct before I do something and hose XP accidently...

---

### Post by Al_Vampyre on 2006-09-03
Thanks for your help guys, managed to get Ubuntu installed and booting by using the alternate cd and telling GRUB to install in /dev/sda1.

---

### Post by Al_Vampyre on 2006-09-04
OK, I spoke too soon, GRUB now appears as expected and Ubuntu loads, as per my post last night, but I can't boot into XP from GRUB either getting GRUB error messages or a Windows hal.dll error whatever drive I try to get GRUB to boot from, any ideas?

---

### Post by xyz on 2006-09-04
I think you should find many answers on this great site:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by unknownsoldierX on 2006-09-17
I just installed Ubuntu using the live CD.  During the install, I did not see any options for the boot loader.

I have Windows on my primary drive, and installed Ubuntu to one of my secondary drives.  I currently have the Vista boot loader installed and would like to keep it.  I will be installing Vista (again) to the same drive as Ubuntu.

Ubuntu is installed, but I can not boot into it.  The Vista boot loader is still in the MBR (good for me).  When I tell my BIOS to boot form the drive with Ubuntu I get a "Error loading operating system" error.  Currently, Ubuntu is the only thing that drive.

I plan on booting Ubuntu using the the Vista boot loader by having it call up the bootsect.lnx, as described here:
[http://www.linuxsolved.com/forums/ftopic17.html](http://www.linuxsolved.com/forums/ftopic17.html)

---

