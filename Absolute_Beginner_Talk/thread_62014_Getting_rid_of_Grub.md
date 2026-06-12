---
title: "Getting rid of Grub"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by mustang on 2005-09-03
Hey guys,

I'm absolutely new to Linux and I hope to get Ubuntu running soon!

As of right now, I have a dual boot system with two hard drives. On my primary, I have xp installed. On my secondary, I have Fedora installed. I would like to put in a new hard drive (for ubuntu) and replace the secondary hard drive. However, if I unplug the secondary hard drive, the grub screen does not come up nor does Windows  boot. I am guessing the MBR is on the secondary hard drive or something?

So I searched on some forums and yahoo for a solution and some involved messing with grub while others with booting using xp's disc, going into the recovery console, and using a fdisk command to restore the mbr. 

So I am confused and trying to be cautious by asking you guys to make sure. I really really don't want to end up losing data on my hard drive that contains XP. 

Thank you very much,

Manish

---

### Post by aysiu on 2005-09-03
First of all, if Grub goes (or whatever boot loader is there goes), the data on all drives is still there.

Most likely, if you install Ubuntu and put Ubuntu's Grub on the MBR, everything should be fine.

---

### Post by mustang on 2005-09-03
[QUOTE=aysiu]First of all, if Grub goes (or whatever boot loader is there goes), the data on all drives is still there.

Most likely, if you install Ubuntu and put Ubuntu's Grub on the MBR, everything should be fine.[/QUOTE]

Hello aysiu, 

Thanks for the quick reponse. The problem is that I would like to put in a new, bigger hard drive for Ubuntu. Doing that involves removing my present secondary hard drive which apparently has the MBR on it...

---

### Post by bjweeks on 2005-09-03
If I'm not mistakeing installing Ubuntu will put the mbr on the new hd and install grub.

---

### Post by Wolki on 2005-09-03
[QUOTE=mustang]The problem is that I would like to put in a new, bigger hard drive for Ubuntu. Doing that involves removing my present secondary hard drive which apparently has the MBR on it...[/QUOTE]

Installing Ubuntu will install grub. Just put in the new hard drive, immediately install Ubuntu and everything should work.

---

### Post by numberexhaust on 2005-09-03
NOTE:  I don't think the MBR can be on a secondary hard drive, I think it needs to be on like the first sector of hd0.  If you're sure you installed grub on the mbr and not on your other hard disk, what could be happening is that grub is crashing every time it tries to detect a disk that isn't there.

Not sure how to fix it or where to go from there   :roll: 

I could try to help with any other questions if you have them.

---

### Post by Steve1961 on 2005-09-05
OK, let me just make sure I understand what you want to do.  You want to keep XP on the first (master) drive and install a new slave drive with Ubuntu.  You then want to dual boot. 

First things first, make sure the only disc in your machine is the XP disc (as master).  Go into the bios and set the machine to boot from your cd drive.  Dig out your XP CD and boot the machine with this in the drive - this really is the only way you can get XP to boot on its own again if you want to leave it as the first hard drive.  After XP setup has set itself up you should get an options screen.  Press R to enter the recovery console.  Once done type fixmbr and let it do its stuff.  You can then reboot (don't forget to remove the XP disc) and windows should boot as normal, as grub will have been removed from the mbr of this disc and replaced by the windows bootloader that was originally there.  

Next, install your second drive.  Boot with the ubuntu CD and install the system onto that drive.  This will also install a newly configured copy of grub on the mbr of the XP drive.  You should now have a working dual boot system.  When you switch on, grub will launch and give you the normal options.  And just to confirm, this shouldn't screw up any of the files on your XP disc.

Finally, there is an alternative if you want to have Ubuntu as the first drive and windows as the slave.  For this to work see my thread here: 

[http://www.ubuntuforums.org/showthread.php?p=334412#post334412](http://www.ubuntuforums.org/showthread.php?p=334412#post334412)

---

