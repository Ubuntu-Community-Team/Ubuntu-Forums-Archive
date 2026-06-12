---
title: "Install issues (Feisty) on Gateway MX6128"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Xusn96 on 2007-07-06
Intel Celeron M 1.5Ghz 1M L2
256MB DDR2 (shared )
intel 910 Vid 8Mb (see ram)
60 GB Hdd

Install on this machine just isn't happening...Short version of the long story: Windows registry got corrupted an win would not boot, shipped with restore on separate partition which we never made the disks for.  Soooooo ... after trying in vain to find an XP Home install disk to repair the install finally decided to just get Ubuntu.
  After initial install prompt screen i get a tannish pink screen with a message box stating " There was an error starting the GNOME settings Daemon...." after a bit the screen goes black and the CD/DVD drive keep cycling away but doesn't seem to do much. 
  I followed the download info to the letter, verified the hash, used the suggested burning app, verified the disk contents, ran memtest.  I ran the live CD on the following system to test the disk:

Pentium II 400MHZ
384MB SDRAM
12GB HDD (Win98)
4.3GB HDD (ubuntu's new home)

...and it installed perfectly with no problems whats so ever.  So the disk is good.

So... do i simply not have enough ram available for GNOME settings daemon.

I have formatted both partitions on the Gateway so they are empty and blank

and yes i am a linux nOOb lol

ty in advance....  X in Wisconsin

---

### Post by robertc36 on 2007-07-06
So what happens on reboot , is is the same.

---

### Post by ugm6hr on 2007-07-06
Ubuntu requires 256MB, so I think it may be that the graphics card is taking enough RAM (out of the total 256MB) to prevent it loading.

I would suggest the AlternateCD or Xubuntu LiveCD.

---

### Post by Xusn96 on 2007-07-06
well nothing. It never gets to the desktop. It goes to the first screen (black) with the ubuntu logo and the 5 or six options on that screen then after 20-30 min the tan screen and the error message comes up anther 5minute s or so later. i have it sitting here next to me like this for about 2 hours now. the Cd drive keeps cycling but the desktop never appears.  My guess at this point is 256MB of shared ram just isnt enough but i dont want to spend the $$ on ram if thats not the issue.

---

### Post by jimbob on 2007-07-06
Some (including myself) have had problems with the live/install CD on certain systems.  You appear to have sufficient hardware to successfully install and run Ubuntu.

If you don't mind a little more work, download and burn the alternate (text install) CD and give that a try - it has always worked for me.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Xusn96 on 2007-07-06
ugm6hr:


Ty for the reply i will try one of those tommorrow. so i guess i can check newegg in the meantime lol

---

### Post by Xusn96 on 2007-07-07
Install is completed. Ran the Alt text installer with no problems. Actual available physical ram was apparently the problem. So no i jus got to get the wireless talking to the router LOL:D

---

