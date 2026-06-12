---
title: "Backup Ubuntu"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-05-22
Hi all,
I have a quick question!
After spending a lot of time customizing my ubuntu (with KDE) the way i want it
to look and behave, I d like to now if there is a way to backup everything
files and setting (all of it) in case of something going wrong or a harware crash,
so if i install the OS again i can bring it back to its current state from that backup
can anyone help/suggest anything???
Many Thanks

---

### Post by ushills on 2007-05-22
Personally I do the following,

Use rsync to backup your home partitions (you should really have a seperate home partition) to your backup media, I use DVD-Ram but you could used CD-RW, DVD+RW etc.  I backup at least once a day and it takes a few minutes

Use "aptoncd" to copy all of your aplications to a CD/DVD, this only needs to be done when you add new software.

Have a LIVE CD handy to reinstall ubuntu if necessary.

I prefer this method as I am able to install a clean ubuntu, then all of the applications i added, then the home folders contain all of my data and the application configuration files.  This also makes it easier after an OS upgrade and backups are quick

---

### Post by Sef on 2007-05-22
You could back up to an external hard drive using either[ Partimage]("http://www.partimage.org/Main_Page") or [Clonezilla]("http://clonezilla.sourceforge.net/").

---

### Post by evkefalas on 2007-05-22
thanks a lot for the suggestions
so for eample if you use say partimage
can u use it to back up and restore while running the os
or you need to use it as livecd or something before booting?
many thanks

---

### Post by Keith Hedger on 2007-05-22
Personally I use a small rescue partition (always handy if u hose your main installation) and dump/restore, I've never been able to get partimage to work properly (I use a powerbook)

---

### Post by ushills on 2007-05-22
One advantage with the method I have adopted is that:

1.  You are not tied into any version of a particular backup software solution, provided you use FAT16 or 32 for the CD/DVD you can get to your files from any machine with a DVD/CD drive without additional software if your hardware fails.

2.  You can just restore a single file, folder, home directory or re-build from scratch with just the CD/DVD you backed up to.

In windows I had to have a hard-drive restored to get the information off it as the backups made in 98 would not restore using the same software under XP as a different version of the software was required for each platform.  Keep it simple, I have over 8000 photos that I cannot afford to lose, I also make archive copies to DVD+R every year.

I rotate the backup of my home directory each week and take it off site.  I also have a script on my desktop to run the backup (you could schedule it with Cron).

You can also as someone has already suggested backup to a second harddrive, but that doesn't help if your PC get stolen, damaged etc.  Although may be ok for everyday use with a DVD backup each week.

---

### Post by Kobalt on 2007-05-22
I like [Simple Backup Suite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") actually.

---

