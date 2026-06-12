---
title: "Backup"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by nhovan on 2008-03-20
I have a Seagate free agent go external hard drive. are there any programs available to back up my system?

---

### Post by Berean on 2008-03-20
Are you looking to just back up files, or are you wanting to make a backup image of your hard-drive?

---

### Post by bumanie on 2008-03-20
If my memory serves me correctly, there have been compatability problems with that drive and ubuntu. However you can try it and see what happens. As far as backup programs go read this
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)
There is also ghost4linux, clonezilla and as long as the drive is large enough, gparted can make a copy of an entire drive or partition. There are also other programs that I can't think of off the top of my head.

---

### Post by notwen on 2008-03-20
You can research Rsync if you like, but if you're fairly new I would recommend QuickStart, a project started by someone here on the forums.  Check this [thread]("http://ubuntuforums.org/showthread.php?t=613462") for more info.  Best of luck.  =]

---

### Post by nhovan on 2008-03-20
both

---

### Post by Berean on 2008-03-20
I've got an external hard drive of the Seagate variety, formatted to 80/135GB.  The first partition is ext2 (or 3) which I have a hard disk image of my internal drive copied to using partimage (download partimage, then just type partimage in the terminal) and follow GUI instructions.  The latter partition is fat32 where I save all my files using Grsync.  Both work extremely well, but I agree Seagates can be problematic.  Mine switches off Hal so each time I use it I have to type sudo /etc/init.d/hal restart.  Despite this mild inconvenience I've very happy with it.  Hope this is of some help. Regards.

To partition the external hard drive I use partition editor (downloadable in system>administration>synaptic package manager) but make sure before you set a disk label that you have any files safely stored.

---

