---
title: "Easy Backup of everything?"
date: 2009-09-04
forum: Apple Hardware Users
---

### Post by brett987 on 2009-09-04
Hello,

I'm pretty much a newbie.  I finally got my G4 with Ubuntu installed, and want to make it a Server (with Gui).  However, I want to know that with going through all this work I can restore my computer in event of Harddrive crash.  I found the SystemRestoreCD but it does not come with Gparted?  I have installed Sbackup and still trying to get the le-web package to work.  Even with program success I do not know if this is going to truly work.

I have very limited experience with command line and want to know with a few commands I can get my complete system back online to the day it was last restored.  Is there a makedisk? or Rsync commands that would work with my backups on an external or a DVD-R?  If so, please help or send me in the right direction for help.  I don't want to be the expert, I just want to know if I type a, b, c=smile.

Thanks a million in advance!
-Brett

---

### Post by djbarroso on 2009-09-04
Hi,

     Depending on what you want to backup (operating system, or data), and how many GB you think your backup will be, you might want to look into using Clonezilla (downloadable from [http://clonezilla.org/](http://clonezilla.org/)). 

     Download the iso, burn it to a CD, and reboot your computer with the CD. It will make an exact image of any partition you choose, or even of your whole hard drive, if you have an external drive with enough space to store it on.

     It is not particularly good for incremental backups, but I can guarantee that, if you make an image of a certain partition, then that partition will be fully recoverable to the exact state in which it was when you made the image. I have tested it myself by making an image, formatting the hard drive, and then restoring the image from a DVD that I burned, and it worked flawlessly. It helps to have 2 or more partitions on your hard drive, because you can work with the partitions separately (operating system vs. data, for example).

     I hope this works for you.

     Cheers!

---

### Post by Gen2ly on 2009-09-04
I still like the classic method:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by brett987 on 2009-09-05
Thanks,  I downloaded and tried both Clonzilla (the stable and alternate Ubuntu) releases, to no avail.  the system just hangs at loading CD-ROM and never continues.  Perhaps this has to do with the Power PC g4 architecture  or Yaboot? I hold the c key down during the bootup process.  Any ideas?  My system can still boot into Ubuntu.



[QUOTE=djbarroso;7899228]Hi,

     Depending on what you want to backup (operating system, or data), and how many GB you think your backup will be, you might want to look into using Clonezilla (downloadable from [http://clonezilla.org/](http://clonezilla.org/)). 

     Download the iso, burn it to a CD, and reboot your computer with the CD. It will make an exact image of any partition you choose, or even of your whole hard drive, if you have an external drive with enough space to store it on.

---

