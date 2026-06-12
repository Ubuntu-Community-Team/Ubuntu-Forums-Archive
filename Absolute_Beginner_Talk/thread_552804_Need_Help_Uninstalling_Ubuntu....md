---
title: "Need Help Uninstalling Ubuntu..."
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by CLUGENHEIM on 2007-09-17
I like Ubuntu, but would like to uninstall it because of lack of disk space. Currently, I have XP Media Edition, and Ubuntu 7.04 on the same HD that is partitioned. I have no XP Media Center install CD, but I have a XP Home Edition one. I also have GRUB installed.

What is the easiest way to uninstall Linux (and the GRUB menu) without screwing up Windows in some way? I need STEP BY STEP instructions, because I'm pretty nooby. =/

---

### Post by p_quarles on 2007-09-17
There's a very good set of instructions in the following link:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Crazy4Coffee on 2007-09-17
What I would do -- and I would always advise lots of caution when formatting and partitioning disks -- is to get a utility called SwissKnife.  It's free.  Actually, search for UBCD.  It's a free project for windows (and I think linux too) that allows you to make a pretty nifty boot cd with a ton of free, useful utilities.  It actually runs kind of a mini-live operating system off the cd that you create from your existing copy of windows.  Anyway, when you boot up the CD, after you make it, it comes with this program SwissKnife, which allows you to manipulate your partitions while there are still systems running on them.  I would just go ahead and delete  or reformat your Linux partition using that program.  Then there are other utilities where you can overwrite that section of your hard drive with 0s or random data for security, or to make sure the system is really gone.  Even if you don't "uninstall" Linux this way, I highly recommend having this tool around.  It saved me when I needed to backup and reinstall systems on my computer.  
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Also, since you mentioned you don't have a Media Center CD, I think there is a way to make a one-time re-install CD.  Try this article: [http://www.howtohaven.com/system/createwindowssetupdisk.shtml](http://www.howtohaven.com/system/createwindowssetupdisk.shtml)
It might be worth doing before you mess around with partitions.

But anyway, that's just what I would do... cause I like a shiny clean disk...

---

