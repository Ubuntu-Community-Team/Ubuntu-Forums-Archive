---
title: "A few problems with 7.04 installation"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by bobsp on 2007-04-28
I've just installed Ubuntu 7.04 on a Windows XP machine to make it dual boot. I've managed the installation, which involved resizing the XP partition, and Ubuntu appears to be running OK, but now when I boot into Windows it runs incredibly slowly. It takes an hour or so for all the sys tray items to finish loading. Has anyone else had this issue, and if so how do I fix it?

Is it possible to make xp the default system rather than Ubuntu?

Also, the ubuntu website said that with 7.04 wireless networking with WPA should "just work". I've looked at the Network Manager. and it doesn't show anything about wireless at all - only wired connections. Why is this?

Thanks,
Bob

---

### Post by Najand on 2007-04-28
If you have resized your windows partition to install ubuntu, there might be some important data of your windows partition has been lost or the windows partition is too small to make virtual memory blocks on it. 
For making windows the default OS, it is kinda easy:
you must edit /boot/grub/menu.lst file. If you copy and paste the output of 
```
/boot/grub/menu.lst
```
ran in a terminal I can help you to set it up.

About the wireless, your wireless card has not been recognised. Its model and information related to it would help us to help you to install neccessory files for using it.

---

### Post by bobsp on 2007-04-28
Thanks Najand,

I resized the partition - which up to that point was the only one - from 80GB to 75% of this - giving approx 20GB to Ubuntu.  The 60GB left to XP should be plenty shouldn't it?  What I don't get it that XP does actually get there eventually, but takes about an hour, with the "egg-timer" on intermittently. If files were removed when I resized, wouldn't that create an error?

Thanks for the tip re the boot order - I'll try that.  I can't remember the model no of the wireless card - I'll look it up tomorrow.

Cheers,
Bob.

---

### Post by Najand on 2007-04-28
Did you defrag your harddisk before shrinking your windows partition?

---

### Post by bobsp on 2007-04-28
Yes I did that, but I think it said there were some files that it couldn't move.

---

### Post by Najand on 2007-04-28
Well, they are system files and they don't usually go to the back side of the partition. Hmm... Was it slow before too?

---

### Post by bobsp on 2007-04-28
No, XP was fine before. Now I'm in the dog house as my son uses XP on this machine :D

---

### Post by paparucino on 2007-04-28
> **bobsp said:**
> No, XP was fine before. Now I'm in the dog house as my son uses XP on this machine :D
Once XP has terminated the setup, does it work normally or everything is slow?

---

### Post by jerrylamos on 2007-04-28
XP tends to use the "scatter" principle in allocating files, a little here a little there a little everywhere.  Defragging tries to make the files contiguous but does not! move them down and leave space at the top.  In particular, on this system, swap turned out to be high in the disk.  I was eventually able to resize this laptop by going into control panel, system, .... and cutting the paging size to zero, i.e. no XP swap at all.  I looked at the defrag detail display very carefully to see how much free space there really was at the top, and then resized down a little less than this amount.  With free space at the top at nearly zero, XP still was using only 56% of the hard disk but the free space was in little pieces all over the place even after several defrags, and a defrag off the internet.

As an investigation, you might bring up XP and cut out virtual memory swap altogether, reboot, make sure it's working O.K. (don't try too much, this system will run O.K. with its 512 mb memory and no swap), and then go in and make a new swap either however XP wants to size it, or at least the size of your memory.

My guess, resizing could have stomped on the existing swap file which is causing XP grief.

Cheers, Jerry

p.s. there is another way around, 
[http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)
which installs Ubuntu as an application on XP.  Instead of partitioning, a big file is allocated on XP which has Ubuntu in it.  According to the writeups, booting up XP, there will be an added option to boot Ubuntu.  I've no experience with this (yet) but there do seem to be a number of users.  To remove Ubuntu from XP, it's a regular XP control panel add/remove programs.....

---

### Post by bobsp on 2007-04-29
> **paparucino said:**
> Once XP has terminated the setup, does it work normally or everything is slow?

Somethings seem to operate at normal speed - like selcting tabs within a multi-tab dialog box, but if you press on the start button it takes ages before the menu appears.

Am in the process of trying jerrylamos' idea. I've set the swap file size to zero. Now waiting the eternity for the system to shutdown, so I can restart and see if that works.

---

### Post by bobsp on 2007-04-29
Unfortunately, playing with the swap file size didn't work.  I set it to zero, rebooted, then set it to auto and booted again (which took like all day !!)  Any other possibilities to try?  What I don't understand is why, if something is missing or corrupted, XP does eventually load all the apps in the system tray, and if I say click on the start button and then control panel, the new window will appear after 15 - 20 minutes.  I've looked in task manager, and the system is 99% idle, and the HDD access light is only blinking occasionally. What the hell is it doing all that time??

---

### Post by bobsp on 2007-05-29
Just to close out this thread, I thought I'd let you know that the problem was caused by a faulty hard drive, which eventually fell in a heap.  New hard-drive formatted properly with appropriate partitions and I'm up and running dual-boot.  Thanks all.

---

