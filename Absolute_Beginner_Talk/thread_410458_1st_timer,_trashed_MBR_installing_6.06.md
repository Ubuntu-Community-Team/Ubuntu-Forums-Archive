---
title: "1st timer, trashed MBR installing 6.06"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Gprof on 2007-04-15
I'm totally new to Linux. Been reading about it for some time, and since MS is wanting all of us to upgrade our OS, thought that I would--from XP to Ubuntu :) Got the 6.06 live CD, but my attempt to install trashed the MBR. Manged to fix that with SuperGrubDisk. I suspect that my setup needs a different install approach since I've added at 2d hard drive and want to keep XP on the main drive, with Ubuntu on a partition in the new one in a dual boot setup that includes a partition for Windows data also. When I tried that, I couldn't boot at all (GRUB error 21). Could still boot from the CD, but neither Ubuntu or XP would boot. Any suggestions would be appreciated. I know nothing of Linux, so many of the discussions on the install forum are meaningless to me at this point. (I've used Mac for 20+ years, as well as DOS and most versions of Windows, but I'm not a "techie"; not intimidated by a command line, just don't know how this Ubuntu/Linux system works yet or any of the commands.) Any help appreciated, or pointers to beginner oriented info for my setup. Thanks.

Dell Dimension 4800; 2.4GHz; 768 meg RAM; 40 gig NTFS HD with XP Home SP2 fully patched; new drive just added (empty) 160 gig--where I tried to install Ubuntu. Have 6.06 live CD and satellite broadband. Also have the 5.10 CD that came with Thomas' *Beginning Ubuntu Linux* (but haven't used that one)--and several older Macs.

---

### Post by freebird54 on 2007-04-15
Well, the idea yoluhave should be fine, that is one of the better ways to dual boot.  However, whichever drive you actually start to boot from should have Grub on its MBR to direct traffic.  Here is a of link that might help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)  this is a GRUB page, but the other pages in there can also help a lot in understanding what's up.

You might also want a look at this thread [http://ubuntuforums.org/showthread.php?t=404358](http://ubuntuforums.org/showthread.php?t=404358)  as it has LOTS of useful links in it!  (when you have time for them all).

Welcome to Ubuntu!

---

### Post by splendid on 2007-04-15
I have Windows 2K on my Raid Setup and actually installed another hard disk for Linux.  If I want to go into Linux, I use the bios to direct the computer to boot from that drive.  My normal bootup drive is Windows.  However, I am using Linux more and more.  This forum is so very impressive.  Everyone is so willing to help each other out.  Microsoft look out.

---

### Post by freebird54 on 2007-04-15
OK - I see a possible source of the problem.  BEFORE you install, open a terminal and type in 
```

sudo fdisk -l
```

(that's an L).  and take note of how the system sees the drive you are installing to.  It will be an identifier such hda or hdb or even sda.  Whatever it sees that drive as, that is where Grub must go.  If it is hda - then grub sees it as hd0, if hdb then it is hd1.  There is a popup asking for Grub's destination when installed - it needs to be told correctly - as it will default to what IT sees as the boot drive at that moment. (it doesn't know you intend to change the BIOS)

That should solve the (immediate) problem.  Of course, if you have the SUper Grub disk you could just use IT to install grub on the correct drive - assuming the rest of the install went OK.

Enjoy!

---

### Post by Gprof on 2007-04-15
Thanks. I'm reading the two pages your referenced. And your 2d post makes sense. I don't remember seeing a pop up for the GRUB drive, but I tried this install last week--and didn't know to look for one anyway. I'll try your suggestions and see what develops. Thanks again.

---

### Post by Gprof on 2007-04-16
Still no luck. I re-ran the installer, etc., but it seems like GRUB isn't getting installed right. comes back with the same error 21. I've been poking around with SuperGrubDisk, and it tells me (I think) that it finds an install of Linux on one of the partitions, but it can't boot it (does a restart when it tries). I can get it to load Windows. 

I didn't find any place in the install process to specify a GRUB location. Not use I understand all the "mount point" stuff either--particularly what should be mounted to each of the several partitions on the 2 hard drives.  I've tried several different things.

If I install GRUB manually (haven't figured out how to do that with SGD yet, but it supposedly can be done?), to what partition do I install it?

Frustrated...

---

### Post by freebird54 on 2007-04-16
Stage 1 of grub should be installed to a drive, not a partition.  In your case, if you're on a separate disk, to that disk.  As for where it went, go into grub itself (at a grub> prompt) and do a 'find'.  Instructions for that should be in the link I pointed you to.  As are the instructions for doing the install.  

It probably doesn't work right now (the find either) because you installed grub over the MBR on the wrong drive(s), and it isn't there to be found on the 'other drive'.

Hopefully it'll all make sense when you get a run throughof the right bit in Herman's howto!

---

### Post by Gprof on 2007-04-16
Not sure what I did, but I *think* I have it working now. Haven't tried rebooting back and forth between xp and ubuntu several times, but on one reboot from SGD, GRUB finally came up. I changed several things (including a bios setting), so not sure which was the necessary step. Thanks for your help.

---

### Post by dstew on 2007-04-16
You sat you installed Ubuntu once, but trashed the MBR. Was the second disk in your system at that time, or did you add it later? What do you mean by trashed the MBR?

One of the toughest problems to solve is getting the grub configuration correct if you install, then add or remove a disk.

---

### Post by Gprof on 2007-04-16
Both drives were installed in the computer when I installed Ubuntu. (I gather from some things I've read that it might have been easier to disconnect the original xp first and then reconnect it after getting Ubuntu up and going.) By "trashed" I mean that nothing would boot, neither xp or Ubuntu. Grub gave error 21. My guess is that it messed up the original MBR since using SGD I was able to repair MBR and boot xp again. I've a fair bit to learn on this new system, but I'm happy that it's now dual-booting correctly and seems to be working well. So on to figure out how to do other things. But they will be other threads!

---

