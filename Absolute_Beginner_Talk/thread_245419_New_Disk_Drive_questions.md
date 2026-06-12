---
title: "New Disk Drive questions"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by SouthernCaliforniaUser on 2006-08-27
I bought and have the Ubuntu Linux CD from LINUX USER Magazine from Fry's, and also purchased a new Seagate 300GB HDD (as in brand new in the box).  When I tried to Format the HDD, it asked me which OS  I was going to install, but LINUX was not one of the choices... only various versions of WINDOWS (like 98, ME, etc), so I aborted the Seagate HDD Utility.  I don't think the drive is formatted yet.

Then I tried booting off the Ubuntu CD... it booted, started loading things, and appeared to install to the HD, but when it said it was booting off the HD, it said 0K (zero K), a message (I didn't write it down), hanged, and then after a very long time, the screen went blank.

What do I need to do?  Should I go back and use the Seagate Utility CD to format the HDD as a, say WINDOWS ME formatted drive, just to get the drive formatted?  Is that what's keeping Ubuntu from installing?

Or... you tell me?

Thank you in advanced.

---

### Post by GuitarHero on 2006-08-27
Ubuntu has to format it to ext3.  You could also download the live gparted cd and partition it with that, but the ubuntu live cd should do it.  Is it an IDE drive or SATA?

---

### Post by SouthernCaliforniaUser on 2006-08-27
It's a Seagate ST3300631A-RK with ULTRA ATA/100 interface.  
I think it is still unformatted.

You say Ubuntu should format it?  
How do I get it to do that?  
What command do I give it?

---

### Post by rutz on 2006-08-27
format using tat utility in fat32 ......ie Win98 format ....after tat put in the ubuntu instalation disk and when it comes to the partioning part delete the formated partion and let ubuntu create its partion automatically..........ie from ur 300gb 756mb will be swap andrest ext3 partion on which ur root will be installed

---

### Post by confused57 on 2006-08-27
> **SouthernCaliforniaUser said:**
> It's a Seagate ST3300631A-RK with ULTRA ATA/100 interface.  
I think it is still unformatted.

You say Ubuntu should format it?  
How do I get it to do that?  
What command do I give it?

Does the live cd(which is probably what you have) work at all on your computer?  The Desktop live cd just runs from ram memory, but you can test the OS to see how well it runs on your system or what kind of configuration changes you may need to do to get the OS to work.  If it doesn't, please list your system specs, especially your video card, mobo, cpu, ram, etc.

I've installed Ubuntu on 3 different completely unformatted Seagate drives "out of the box" new with no problems, just using the Ubuntu installation cd.

---

### Post by SouthernCaliforniaUser on 2006-08-27
Ahhh...  I discovered the problem: I had my CD Drive on the same cable as the HDD, and apparently that is NOT workable.  

I have a 2nd CD on a separate I/F Cable from the HDD, and when I put the Ubuntu CD into that other CD Drive, then things ran to completion.  

BTW, I had already gone ahead and partitioned the HDD with the Seagate Utility, and was forced to limit the partion size to 137GB.  Maybe that helped, but I don't know for sure.  It may have been unnecessary.

In any event, Ubuntu asks partition selection/action during the INSTALL (when you run from CD), and I chose ERASE ALL (the entire HDD's 300GB)...  which automatically also selected creation of: 
- Partition #1 (/dev/hda ext3), and
- Partion #5 (/dev/hda swap).  

I hope this is OK and will allow Ubuntu to function freely (300GB is a LOT of room!!).

BTW, I read suggestions of creating three partitions, of 200MB, 700MB, and the rest of the HDD for a third partition (details are kind of fuzzy right now).  Do I need to do these tweaks after the INSTALL (I think one was for the root, the 2nd for a swap area, and I don't know the purpose of the third partition)?

I don't know the two existing partition size(s) (yet), as Ubuntu is still chugging away at performing the System Install (yea!! :D ).  I expect once it is done, I can remove the Ubuntu CD, and reconfigure my PC to boot off the HDD, coming up normally (such as it is) without the CD anymore.

Thank you for helping me.  I hope this will keep someone else from doing the same mistakes I did.

Ubuntu LINUX, here I come... !!

---

### Post by confused57 on 2006-08-27
You might want to check out this website:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Read over the sections on "Plan partitions", "Installing Dapper", etc.

Another great website to check out, or at least bookmark:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
This is much more than just a dualboot site, lots of good info.

Here's some info:
[http://www.ubuntuforums.org/showthread.php?t=182716](http://www.ubuntuforums.org/showthread.php?t=182716)

You might want to consider setting up a separate home partition eventually...root(/) maybe about 10 Gb, swap(approx 1 Gb), home the rest, or a separate partition just to store data & documents...just some ideas for later.  Enjoy using Ubuntu, I've never had so much fun with computers.  Don't hesitate to ask questions, plenty of knowledgable people here willing to assist.

---

