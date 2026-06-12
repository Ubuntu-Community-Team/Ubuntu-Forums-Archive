---
title: "newbie question"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by tlcmd on 2007-11-23
Currently I have 4 computers on my home network via Homeportal 1100 using 2wirepc USB devices.  3 of the 4 are running WindowsXP, the 4th is running Windows98 se. 

Computer #4 is an old Quantex, Pentium III, 550 MHz, with an 18.6 Gig Hard drive. It is a 'guest' computer to be used by visitors (usually grandkids). I would like to learn more about Linux with some hands on experience via Ubuntu. I have just wiped the hard drive of old #4 and re-installed Windows98 se and the software for the soundcard and 2wirepc USB device. Leaving essentially 18 Gigs clear. I have the new (7.10) Ubuntu installer on a cd. 

Should I partition the Hard Drive prior to installing Ubuntu?
And will it work with the Homeportal 1100 modem/router?  
Or  if I completely reformat C: (removing Windows) and then using the cd-rom installer, will it connect via the 2wirepc and Homeportal 1100 modem/router so I can download the rest of the program? 

Any comments, suggestions,step by step instructions, and even snide remarks would be appreciated.

Thanks, I'm certain I'll have more questions later.
tlcmd

---

### Post by jken146 on 2007-11-23
Try this guide. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I don't know about your router, but I'd b surprised if it didn't work at all on your LAN.

---

### Post by natehatewindows on 2007-11-23
Ubuntu has a good partitioner built in. you can use that and wont have any problems. if you decide to use another program to partiton i would reccomend gparted. just google it and it has a bootable disk that is super great.

---

### Post by ugm6hr on 2007-11-23
@tlcmd:
Looks like you want to keep Windows98 and dual-boot with Ubuntu7.10.  If you have already installed W98 on a single partition, I would recommend GParted LiveCD to resize (make smaller) the W98 partition, leaving at least 10GB as "empty space" (or is it "unallocated" - can't remember what GParted calls it).

Then just boot using the Ubuntu CD, and use the "Guided - Use largest continuous free space" installation option when it asks.

When you reboot, you should be offered both options (Ubuntu or W98 ).

As for the router - I have never known there be an issue with any Linux.

PS: It is possible to resize partitions from Ubuntu LiveCD, but I have never used it reliably.

EDIT:
You also mention wiping the C: drive.  If you don't want W98, then just put the Ubuntu CD in and ask it to use the whole HD.  No need to partition.

---

### Post by samuel.rajesh on 2007-11-23
you can try out Wubi ([http://wubi.sourceforge.net/](http://wubi.sourceforge.net/)) ,that way u install it without partioning

---

### Post by hyper_ch on 2007-11-23
If you want to partition and if you have any important data on it: **MAKE A BACKUP FIRST!**

Once you have that backup, defrag 2-3 times the drive in windows. Then you can use the ubuntu partitioner for resizing and setting up the new partitions.

---

### Post by natehatewindows on 2007-11-23
> **hyper_ch said:**
> If you want to partition and if you have any important data on it: **MAKE A BACKUP FIRST!**

Once you have that backup, defrag 2-3 times the drive in windows. Then you can use the ubuntu partitioner for resizing and setting up the new partitions.

YES! these are the two most important things!!

---

### Post by tlcmd on 2007-11-23
Thanks for the prompt replies. This computer is "clean". Windows98se, sound card drivers, and 2wirepcUSB drivers. No files to back up. The hard drive was formatted and only the above have been loaded. I'll try to download Ubuntu with the installer off the cd. I'm sure more questions will follow.
Thanks again.
tlcme

---

