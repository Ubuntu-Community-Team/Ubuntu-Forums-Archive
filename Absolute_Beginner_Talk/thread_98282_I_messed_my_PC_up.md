---
title: "I messed my PC up"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by SweetDreams on 2005-12-02
Well, I installed Ubuntu over my Windows partition a few times. A few installations didn't go well, but I had an AMD64 Ubuntu 5.04 installation go semi-well except for the fact that my user account wasn't able to sudo. So I installed Ubuntu x86 5.04 Ubuntu over that, and it was going fine until I tried to update to Breezy Badger. I restarted in the middle of the update, and I guess that messed a few files up, so I tried to reinstall x86 Ubuntu and it froze in the middle of the installation.
Yes, I am a newbie to Linux. I do not know what to do with my PC.
It's a nice PC, and I want it to perform well. I'll post the specs..
AMD64 2800
1 GB PC3200 DDR RAM
nVidia Geforce 6800 GT 256 MB GDDR3
Creative Sound Blaster Audigy 2
Chaintech VIA SKT800 motherboard
Two SATA 10,000 RPM Hard drive's supposedly in RAID 0.
I don't know what to do! Can I just erase everything off my hard drive completly, and start over with a fresh HD? I'd be glad to install Ubuntu x86 again afterwards, but christ this is a nightmare.:(

---

### Post by teaker1s on 2005-12-02
google and download fdisk delete any partitions and then take a look at fake raid [here]("https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28fakeraid%29") because that how you install on your drive type

---

### Post by SweetDreams on 2005-12-02
I downloaded fdisk, and it's an .exe and I'm on a Ubuntu Live CD right now, so I really can't get into Windows and do that. I don't have Windows anymore either, so yeah.
EDIT: I will donate 25 USD via paypal to the person who helps me with this.

---

### Post by choptop on 2005-12-02
Just a suggestion, if you can get here you should be able to to find a DOS BOOT image on the web some where to download to run off a floppy or CD which will allow you to run FDISK

---

### Post by SweetDreams on 2005-12-02
[QUOTE=choptop]Just a suggestion, if you can get here you should be able to to find a DOS BOOT image on the web some where to download to run off a floppy or CD which will allow you to run FDISK[/QUOTE]
Is there anyway I can erase the crap off my HD without using FDISK.

---

### Post by cychem1 on 2005-12-02
Go to Bootdisk.com for floppy or [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) if you do not have a floppy drive. 

Reboot Computer with floppy or CD in drive

From either the boot floppy or the CD

Run fdisk

Delete offending partition
Exit remove cd or floppy
Reboot and install ubuntu

woo hoo

Just thought of an alternate routes

use the install cd or floppy that came with your hardrives(for installation) most manufactures have utilities that wil wrtie zero's to the drive. I western digital does its and option to write zero's to the drive. You may have to disable the raid configuration in the bios before you do this. 

This method will erase all data on your harddrive not just on a single partition so be very sure this is what you want to do. YOU HAVE BEEN Warned!

You can also boot from a windows xp cd and when its gets to the part where you pick  install or repair pick repair. run fdisk at command prompt

---

### Post by TeeSeeJay on 2005-12-02
[QUOTE=cychem1]Go to Bootdisk.com for floppy or [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) if you do not have a floppy drive. 

Reboot Computer with floppy or CD in drive

From either the boot floppy or the CD

Run fdisk

Delete offending partition
Exit remove cd or floppy
Reboot and install ubuntu

woo hoo[/QUOTE]

Another vote for the ultimate boot cd. That thing is awesome.

But there's gotta be a partition tool on the Ubuntu live CD, doesn't there? I dunno, it seems as though there should be.

---

### Post by SweetDreams on 2005-12-02
[QUOTE=cychem1]Go to Bootdisk.com for floppy or [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) if you do not have a floppy drive. 

Reboot Computer with floppy or CD in drive

From either the boot floppy or the CD

Run fdisk

Delete offending partition
Exit remove cd or floppy
Reboot and install ubuntu

woo hoo

Just thought of an alternate routes

use the install cd or floppy that came with your hardrives(for installation) most manufactures have utilities that wil wrtie zero's to the drive. I western digital does its and option to write zero's to the drive. You may have to disable the raid configuration in the bios before you do this. 

This method will erase all data on your harddrive not just on a single partition so be very sure this is what you want to do. YOU HAVE BEEN Warned!

You can also boot from a windows xp cd and when its gets to the part where you pick  install or repair pick repair. run fdisk at command prompt[/QUOTE]
I'll try the Windows XP route. Thanks, I didn't think of that.

---

### Post by cychem1 on 2005-12-02
He could try gparted but that is not installed by default not sure of its status on the live CD

sudo apt-get install gparted ( might work from live cd ???)

Also if you have a copy of Partition Magic 8.0 the cd is bootable and it will let you configure the harddrives and format as well. Linux filesystems are also supported.

---

### Post by TeeSeeJay on 2005-12-02
[QUOTE=cychem1]

You can also boot from a windows xp cd and when its gets to the part where you pick  install or repair pick repair. run fdisk at command prompt[/QUOTE]

That won't quite work. That's not a real command prompt you get, it's the XP "Recovery Console" which gives you a limited toolset, of which fdisk is not a part. However, diskpart is present and you can use it to manipulate the HDD. See this for more info: [http://support.microsoft.com/default.aspx?scid=kb;en-us;314058](http://support.microsoft.com/default.aspx?scid=kb;en-us;314058) , particularly the "available commands" section.

Another idea with the XP disk is just go through the setup process until you get to the disk setup portion, delete the partition there, and then reboot without continuing with Windows setup.

---

### Post by musther on 2005-12-02
If you want to start from scratch, just stick in your ubuntu install CD, boot using it, during the install process, the bit when you set up your drives, either tell it to wipe the drive and use it all for ubuntu, or select manual partitioning, that'll let you delete all your partitions and start again.  Alternatively, (assuming cfdisk is on the live cd here) boot the live cd, open a terminal, type cfdisk, and use that to deal with your hard drive(s).

---

### Post by ubuntu_demon on 2005-12-03
IMHO the easiest way to solve this is :
1) backup your personal files (at least make sure you have a seperate /home partition). If you can't boot into ubuntu use a live cd to acces your files.
2) reinstall

---

### Post by SweetDreams on 2005-12-03
You guys are offering a bunch of different ways to do this, and really thank you. I appeciate your help. I'm going to try most of them now, and see if they work. I'm sure a good nights sleep has let my patience recover, lol.

---

### Post by SweetDreams on 2005-12-03
I tried doing it with the Ubuntu install discs, and that didn't work too well. I've tried installing Ubuntu 4.10(x86), and Ubuntu 5.04(AMD64/x86). It keeps telling me a GRUB error has occured after the installations. The last one I had was Error 22. I guess I should check the wiki or something.
Hahaha yeah! Nothing on that in the Wiki, or I'm just really bad at searching..

---

### Post by cychem1 on 2005-12-03
Try using windows 98 boot floppy from boot disk .com Make sure your bios is set to boot from floppy first.

Then run:

fdisk /mbr

That should correct the grub error.  Then retry install of ubuntu

This should also work from the  ultimate boot CD

If that fails then

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Nuke the harddrive

If that fails you might have to start trouble shooting hardware.

Good Luck

---

### Post by SweetDreams on 2005-12-03
Mmm, I inserted a Windows 98 boot disk. It's a few years old, but yeah it would probably start properly if my computer was fucked. So anyways, I started the disk.
It says that C:\WINDOWS\COMMAND.EXE is missing.

---

### Post by ubuntu_demon on 2005-12-04
This is the easiest way to get back on track :

back up all your important documents(using a live cd for example). Now reinstall windows -> remove all partitions during partitioning ,leave some unpartitioned space for Ubuntu. Now reinstall Ubuntu breezy on that unpartitioned space.

---

