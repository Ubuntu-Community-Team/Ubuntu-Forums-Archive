---
title: "Force Disk Check, now stuck Help I want to like ubuntu!"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Dunover on 2008-01-24
I  have been testing ubuntu for a couple of week now, I have it install on a slave drive... it seems to be working pretty good except every time have booted I have to "find" my hard drives and type in admin password before I can use them. then they appear on the desk top

Now today while booting it says something like

"this hard drive has been mounted 29 times with out checking now forcing check"

then is starts to check and stops and hangs somewhere with a percent on the right, I have tired about 5 -6 times even in Safe mode. still stops and hangs some where along the process

am now in win2kw with the drive in question..so know it is working fine!!

Help is ubuntu too buggy? Say it not so!! I so want to kill thewin

Cori

---

### Post by emarkd on 2008-01-24
Ubuntu is set up to do that check on a regular interval,and it's important that you allow it.  If your computer has crashed or been turned off without shutting down properly, the check may find errors and take a long time to repair.  How long have you let the check run before deciding it's not working?

---

### Post by Nythain on 2008-01-24
yeah, i was gonna ask how long do you let it run before it appears to "hang"
it could more than likely just be finding/fixing any errors it comes across... its a pretty important though annoyingly long procedure, nothing sucks worse then when you boot up to browse the web and it force checks a 500gig hard drive :(

my advice, let it run for a while, i mean, if its still "hung" after like 1-2 hours then there's a problem somewhere.

as far as the mounting them bit... have you considered adding them to your fstab so they will automount everytime you boot up if they are available??? just google "fstab" or "auto mounting hard drives in ubuntu" should get you a few good guides on this subject

---

### Post by emarkd on 2008-01-24
There are several tools available to determine when the next scan will occur.  I like showfsck.  It's a simple command line app that will report the number of reboots left before the scan will run.

---

### Post by Kilz on 2008-01-24
[AutoFsck is another application]("https://wiki.ubuntu.com/AutoFsck") to adjust the fsck settings. One nice feature is that it can make the scan come as your shutting down. That way you can walk away and let the scan happen, instead of at the boot up when you want to use the computer.

---

### Post by Dunover on 2008-01-24
maybe I will let it check tonight....am working during the day and cannot afford to be down for that long :(  Does ubuntu do this often?
 Sadly on w2k now
Corisa

---

### Post by smurphy_it on 2008-01-24
It 's the EXT3 file system which causes the "Forced Check" and not the Ubuntu O/S.  Any other Linux distro with an EXT3 file system would behave the same.

---

### Post by Herman on 2008-01-24
I recommend using either the Ubuntu Live CD with GParted in it, or the standalone [GParted -- LiveCD]("http://gparted.sourceforge.net/").
Open GParted.
Then simply right-click on the partition you want checked and repaired and click 'Check' from the right-click menu.
Then click 'Apply' on the toolbar, and hit the 'Apply' button in the confirmation window.
That will run e2fsck for you with much more effective options than fsck can use for your ext3 file sysem and reset your superblock counter for you.

You can do that anytime you like, it's a simple thing to do and it will keep your file system in top shape.

Regards, Herman :)

---

### Post by jken146 on 2008-01-24
For not having to mount your partitions with a password every time, see
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
and/or
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Mitchlb on 2008-01-24
If you set it up on one drive, you should get a program that allows you to switch between Ubuntu and (XP????). Dual boot. The best solution is set up a raid array and dual boot both operating systems. (Especially if both hard drives are equal). Mainly though, make sure the hard drives are interacting. You can't just put one os on each hard drive and expect it to work properly. Hope that helped. 

Good luck!

---

