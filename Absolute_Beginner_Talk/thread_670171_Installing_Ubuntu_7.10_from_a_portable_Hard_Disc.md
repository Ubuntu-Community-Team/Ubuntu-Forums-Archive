---
title: "Installing Ubuntu 7.10 from a portable Hard Disc"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Vishesh on 2008-01-17
Hi.

I'm trying to install Ubuntu 7.10 from a portable USB hard disc I own (Yes my computer can boot from a USB device). The Hard disc currently has around 1 gb free space. I'm currently using Windows XP. And I do not own a CD drive. 

I read [this guide]("https://help.ubuntu.com/community/Installation/FromUSBStick"). But making an executable from the script given ( executable means saving it as a ".exe" . right ? ) did not work. (By did not work I mean nothing happened)  This is the script I used.
```

wget http://www.startx.ro/sugar/isotostick.sh
chmod 755 isotostick.sh
sudo ./isotostick.sh ubuntu-7.10-desktop-i386.iso  I:\

```

The "isotostick.sh" file was present in the same directory as this ".exe" file and so was ubuntu-7.10-desktop-i386.iso. But nothing seemed to happen. 

I even read other guides from which you could install it directly from windows (modifying boot.ini and all ) But in all of those guides it seemed as though I would need to download Ubuntu all over again. Which would be quite a hassle as  my Internet connection is not that fast and it would take a min of 10 hours.

So I would really appreciate if someone could help me out. Please.. :(

EDIT : Just thought I'll let you know I'm trying to Install it on my hard drive ( E: ) which has around 30 gb of free space and is completely empty and is an NTFS drive. I: drive is the portable hard disks drive.

EDIT : I realized I needed to make the isotostick.sh file into an exe file. SO I opened it with notepad and saved it with the same name but as a .exe file. Then I ran it using Run and I:/isotostick ubuntu-7.10-desktop-i386.iso I:\ but nothing seems to be happening. Just a blank screen.

---

### Post by ByteJuggler on 2008-01-17
> **Vishesh said:**
> Hi.

I'm trying to install Ubuntu 7.10 from a portable USB hard disc I own (Yes my computer can boot from a USB device). The Hard disc currently has around 1 gb free space. I'm currently using Windows XP. And I do not own a CD drive. 

I read [this guide]("https://help.ubuntu.com/community/Installation/FromUSBStick"). But making an executable from the script given ( executable means saving it as a ".exe" . right ? ) did not work. (By did not work I mean nothing happened)  This is the script I used.
```

wget http://www.startx.ro/sugar/isotostick.sh
chmod 755 isotostick.sh
sudo ./isotostick.sh ubuntu-7.10-desktop-i386.iso  I:\

```

The "isotostick.sh" file was present in the same directory as this ".exe" file and so was ubuntu-7.10-desktop-i386.iso. But nothing seemed to happen. 

I even read other guides from which you could install it directly from windows (modifying boot.ini and all ) But in all of those guides it seemed as though I would need to download Ubuntu all over again. Which would be quite a hassle as  my Internet connection is not that fast and it would take a min of 10 hours.

So I would really appreciate if someone could help me out. Please.. :(

EDIT : Just thought I'll let you know I'm trying to Install it on my hard drive ( E: ) which has around 30 gb of free space and is completely empty and is an NTFS drive. I: drive is the portable hard disks drive.

No, isotostick.sh is a shell script for the Linux shell (e.g. it's the equivalent of a batch file on Windows.)  As such it won't run on Windows.  That script is useful for making a bootable USB stick of Ubuntu, from  within an already running Linux/Ubuntu installation.  You cannot make an .exe file simply by renaming a file!  

You need to follow the instructions under "Preparing the Flash Drive manually" using Syslinux, which has a windows version as well.

Note: You'll have to copy the *contents* of the ISO image to your USB stick, as noted in the instructions.  Obviously you dont have a CD drive, so you'll have to use a CD emulator (like [Daemon tools]("http://www.daemon-tools.cc/dtcc/download.php")) to allow you to mount the .iso image, in order to copy the contents of the ISO image onto the USB stick. (Alternatively some archivers can open .iso files, I *think* Winzip does (unverfied.))

Note 2: Some of the instructions refer to the Dapper release of Ubuntu, you would probably have to adjust that to reflect the fact you're installing a later version of Ubuntu.

Note 3: Linux uses its own filesystem, so your blank Windows NTFS partition E: will be deleted and ultimately replaced with (probably) a Linux EXT3 partition.  The contents will not be readable by Windows as Windows doesn't know how to read EXT3 by default.  (That said, there are drivers that will allow Windows to see Linux partitions but you can ask about that later.)  Linux has no problem seeing/using NTFS partitions however.

Note 4: Once you get to the installer, make sure you **DO NOT **choose "guided - use entire disk" as that will format your entire disk including Windows and therefore delete all data you currently have on the disk.  The best would be to probably use "Use largest available free space" or even "Manual partitioning", and then ask for advice here. 

Note 5: It is a good idea to make a backup of all critical data from your Windows partition, just as a precaution, in case of disaster, before doing anything else.

---

### Post by kpkeerthi on 2008-01-17
-- author removed dup post --

---

### Post by Vishesh on 2008-01-18
Uhm alright I understood all that was written and I would follow it too. But a major problem seems to have cropped up !!

Before I read your reply I tried the same thing on a laptop thinking maybe dos is screwed up on the desktop. And well the laptop hung up !! SO I got a little infuriated and closed to lid of the Laptop..

Later on when I switched it on I got an error message saying "Delayed write Failed". I've got this many times so it wasn't anything big all I had to do was reconnect the hard drive. 

Unfortunately on doing so I got that error message again and when I would try to open the hard drive it would be BLANK. The statistics showed 97 GB used .. 450 MB free. But I couldn't see any data !!

THIS IS SERIOUS !!

I tried it out on other computers and either the comp hangs up or The delayed write message comes and then I get to see the Blank drive !!

A little help please !!!!!!!

---

### Post by ByteJuggler on 2008-01-18
> **Vishesh said:**
> Uhm alright I understood all that was written and I would follow it too. But a major problem seems to have cropped up !!

Before I read your reply I tried the same thing on a laptop thinking maybe dos is screwed up on the desktop. And well the laptop hung up !! SO I got a little infuriated and closed to lid of the Laptop..

Later on when I switched it on I got an error message saying "Delayed write Failed". I've got this many times so it wasn't anything big all I had to do was reconnect the hard drive. 

Unfortunately on doing so I got that error message again and when I would try to open the hard drive it would be BLANK. The statistics showed 97 GB used .. 450 MB free. But I couldn't see any data !!

THIS IS SERIOUS !!

I tried it out on other computers and either the comp hangs up or The delayed write message comes and then I get to see the Blank drive !!

A little help please !!!!!!!

**Even though this is not a Windows forum, I'll provide [B]the following Windows only comments/help:**[/B] (I state this so other people reading this post will not mistakenly think this applies in any way shape or form to Linux.)

"Delayed write failed" means the operating system cached data in its write cache for the hard disk in question, but lost the connection to the drive before being able to actually physically write the data to the disk.  If the failed write had to do with updating the NTFS filesystem structures themselves then it's quite possible that the filesystem on the physical disk is now in a semi-corrupted/inconsistent state, hence why you now can't see any contents on it.  

For this reason, you should never allow this sitation to occur to prevent possible data loss.   For external hard disks or disks that can be disconnected during a machine being in sleep/suspended state, you should always disable write caching on the disk to minimize/prevent this from happening.  You can usually set this on the propery pages of the hard disk drive driver, in the hardware device manager in Windows, in the Control panel.

If I was you I'd boot up with the Windows XP CD into the recovery console, and run the following from a command prompt:

```
chkdsk d: /s
```

Replace d: with whatever is the drive letter of your external disk.

---

### Post by Vishesh on 2008-01-20
> **ByteJuggler said:**
> **Even though this is not a Windows forum, I'll provide [B]the following Windows only comments/help:**[/B] (I state this so other people reading this post will not mistakenly think this applies in any way shape or form to Linux.)

"Delayed write failed" means the operating system cached data in its write cache for the hard disk in question, but lost the connection to the drive before being able to actually physically write the data to the disk.  If the failed write had to do with updating the NTFS filesystem structures themselves then it's quite possible that the filesystem on the physical disk is now in a semi-corrupted/inconsistent state, hence why you now can't see any contents on it.  

For this reason, you should never allow this sitation to occur to prevent possible data loss.   For external hard disks or disks that can be disconnected during a machine being in sleep/suspended state, you should always disable write caching on the disk to minimize/prevent this from happening.  You can usually set this on the propery pages of the hard disk drive driver, in the hardware device manager in Windows, in the Control panel.

If I was you I'd boot up with the Windows XP CD into the recovery console, and run the following from a command prompt:

```
chkdsk d: /s
```Replace d: with whatever is the drive letter of your external disk.

Thanks a lot for the information. My hard Drive is now running perfectly !! :)
But I have haven't managed to install Ubuntu.
Reason - The Portable Hard Drive is of NTFS format !! 
Is there any way I can still install from it ?  :confused:

Otherwise 

I Plan to install it directly from windows [*guide* ]("https://help.ubuntu.com/community/Installation/FromWindows")using the CD Approach. Which requires me to download the alternate Ubuntu Install CD. Damn ..

Anyway Thanks :)

---

### Post by ByteJuggler on 2008-01-20
> **Vishesh said:**
> Thanks a lot for the information. My hard Drive is now running perfectly !! :)
But I have haven't managed to install Ubuntu.
Reason - The Portable Hard Drive is of NTFS format !! 
Is there any way I can still install from it ?  :confused:

Otherwise 

I Plan to install it directly from windows [*guide* ]("https://help.ubuntu.com/community/Installation/FromWindows")using the CD Approach. Which requires me to download the alternate Ubuntu Install CD. Damn ..

Anyway Thanks :)

You should be able to format your external disk as FAT32 instead of NTFS, and then the usb install procedure should work.  However I realise you have a lot of stuff on you external disk, so thats probably not the easiest of things to accomplish.  Better would be to buy a 2GB or 4GB USB memory stick, and then make that bootable, and install ubuntu from that.

---

### Post by ByteJuggler on 2008-01-21
Hello, I happened to come accross this tonight:

[http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/](http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/)
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Seems the simplest methods so far.  Good luck.

I've also found this: [http://www.pendrivelinux.com/2007/11/04/usb-pendrive-linux-install-from-windows/](http://www.pendrivelinux.com/2007/11/04/usb-pendrive-linux-install-from-windows/)

Instructions from Windows. Not sure if it will help with Ubuntu though.

---

### Post by Vishesh on 2008-01-22
Thanks for the Info but I just finished installing Linux and fixing Windows. ( I kinda crashed my Windows while trying to install Linux from Windows .. then I finally had to just buy a pen drive and install Linux through that .. and then revert all the changes I had made to Windows for it to work )

I always thought I wouldn't have a lot of problems installing Linux .. guess most people don't. It would have been a hell of a lot easier if my CD-ROM drive was working. Oh well 

Now the only thing left to do "Learn how to use Linux". The terminal commands and quite a lot of things still elude me. 

Thanks again ... for all your help. :)

---

### Post by just_bruce on 2008-02-14
Can i install Xubuntu Gutsy with XO from its live cd? it is on a windows machine but I have no problem with eliminating windows.  which partitioning choice should i make?
bruce

---

