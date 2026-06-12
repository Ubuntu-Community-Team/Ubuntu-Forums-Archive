---
title: "Dual Booting Help"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by SOG420 on 2006-04-25
Could someone point me towards a howto or instructions as to how to dual boot Fedora Core 4 and Ubuntu Breezy Badger. Thanks again.

---

### Post by NeoGreen on 2006-04-25
Okay, I am new to Linux, but this is what I did.  I usually use Windows XP to help me with my partioning.  I have a computer that has XP, Ubuntu and Debian running as a triple boot.  What I did was first install Windows and create three different partitions. After the installation of XP, I then installed Ubuntu and finally Debian.  Grub lets you gives you the option to choose which partition to use.  This is the way I know how to do it, I tried doing it under Ubuntu when asked to partion but I got lost.  If you don't want to keep or install windows, just use the partion part of the installation, create two partions then abort install.  Your partions you created will not erase.  Then install Ubuntu to one partion then Fedora to the other.  Sorry I am new to Linux and this is the way I created my monster triple boot.:-|

---

### Post by nalmeth on 2006-04-25
Likely, I would assume Fedora is using the EXT3 filesystem?
Backup any important data you might have before you do anything..
Use a liveCD like knoppix or gparted to use a free partitioning tool, and resize your fedora to give enough space as you see fit for your ubuntu.
then use the ubuntu installer, and tell it to use the free space on the drive.

---

### Post by SOG420 on 2006-04-25
Currently I have installed Ferora w/ ext3 filesytem on the first hard drive and I want to install Ubuntu on another drive and be able to boot both. Any advice?

---

### Post by nalmeth on 2006-04-25
ahh different drives. I C 
The Ubuntu installer will work just fine. So long as you don't have data you need on the second drive.
If Fedora is your primary, it should probably be named 'hda' or 'sda'
your second (slave) drive should be named 'hdb' or 'sdb'
With the ubuntu installer, just make sure that ubuntu installs on hdb
When it comes up, tell grub to install on the primary harddrive.
In the unlikely event you are unable to boot fedora after this, check this out to install grub.
[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=grub+install](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=grub+install)
JUST MAKE SURE YOU KNOW WHAT DRIVE YOUR FEDORA IS ON, AND TELL UBUNTU TO INSTALL ON THE *OTHER* DRIVE. The installer will take care of the rest

---

### Post by SOG420 on 2006-04-25
Ok a couple hours later with no progress so far I decided to do a fresh install of both OS's installing Ubuntu first and Fedora second. When the Grub menu appears it only sees Ubuntu. I realize this is a Ubuntu Forum but I really would like to have Fedora for school.  The link  about Grub (above) is if Ubuntu won't boot. Fedora is the unseen one so I'm kinda lost?

---

### Post by nalmeth on 2006-04-25
I'm sorry I can't help you more, but:
 Did you install Fedora on the primary again, or did you switch it around this time?
Using the reinstall grub trick, and telling it to install grub on the primary harddrive or partition should create an entry for that OS on grub.
AFAIK
If you've tried this already, then I'm afraid you'll have to wait for someone more knowledgeable, or try the fedora forums.
I'm suprised more people haven't responded yet.. This must be some sort of slow hour in the Beginner talk forum.
:confused:

---

