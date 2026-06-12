---
title: "Need an automated backup method"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by TreverT on 2007-11-01
Warning - Newbie here.  :)

I am trying to switch from XP to Ubuntu.  Going well so far, but I have run into a problem in an unexpected area - backups.  In XP, I used the freeware utility Syncback, which just sat in the taskbar and automatically backed up my chosen files to my chosen locations at time intervals I set.  It could backup to local hard discs, FTP sites, and even email accounts online.  Plus, I had my various rules set so that it would, for example, backup really commonly modified files like our business records every ten minutes to both local discs and FTP, but just backup infrequently-changed directories (music, photos) once a week or so.  A really handy utility and great peace of mind.

In looking for something similar in Linux, I have found Pybackpack and Simple Home Backup, but both seem very limited.  Pybackpack must be manually run and can't do automated backups, and it seems to want to erase the destination discs before writing the backup!  :(  Simple Home Backup is better, but it still wants to put everything in just one location, rather than handling sending backups to both local discs and FTP sites.  

Does anyone know of a way to do what I need?  I have seen some people refer to making scripts and editing cron (???) to do this without need for any GUI utility, but that is way over my head unless someone can supply very step-by-step instructions.  

Thanks in advance for any help!

---

### Post by greg963 on 2007-11-01
try unison or unison-gtk (graphical), I haven't used it myself, but I hear its handy.

---

### Post by ushills on 2007-11-01
have a look at [http://dev.riseup.net/backupninja/](http://dev.riseup.net/backupninja/).

This is very customisable and will run automatically.

I have a few more detials on my site here [http://www.ushills.co.uk/ubuntu/backupninja.html](http://www.ushills.co.uk/ubuntu/backupninja.html)

My setup keep the last 90days as incremental files.

---

### Post by Hospadar on 2007-11-01
If you just need to copy files to a certain location, and you are comfortable using the command line (or are willing to learn) you could use cron jobs (with the "crontab" and "cron" programs) to do regularly scheduled simple operations.

You'd want to do some reading into this, it's probably not the best solution if you want a system-restore type situation or a backup scheme more complex than just file copies.

---

### Post by TreverT on 2007-11-01
> **Hospadar said:**
> If you just need to copy files to a certain location, and you are comfortable using the command line (or are willing to learn) you could use cron jobs (with the "crontab" and "cron" programs) to do regularly scheduled simple operations.

You'd want to do some reading into this, it's probably not the best solution if you want a system-restore type situation or a backup scheme more complex than just file copies.

File copies are all I want.  Just something to copy, say, the /user/doc/moneyfiles directory to a spot on another hard disk, and also to my FTP space online.  

Boy, this thread went over my head reeeeally fast...  Let's see if I can follow along:

I Googled for unison-gtk and found this link:
[http://packages.debian.org/stable/net/unison-gtk]("http://packages.debian.org/stable/net/unison-gtk")
But...  I don't even understand what I'm looking at there.  I can't tell which is the actual unison program, nor what else I need.  It looks like I'd have to install all those red-dotted extra libraries just to make it work?  I'm coming from the land of backupinstall.exe, remember...  :confused:

I also looked at the backupninja site.  It *looks* like it might work for me, if I'm correctly understanding that the cron.d directory is just a repository for scripts to run on a scheduled basis, and backupninja is just a collection of scripts to drop in there.  I think.  But it looks pretty confusing.  

I'm off to read up on just what cron is now...

---

### Post by digitalbenji on 2007-11-01
Both Bacula and BackupPC are free and available in apt, and both will do this, although require some configuration.

---

### Post by TreverT on 2007-11-01
I looked at both, but they were way beyond my needs and way over my head.  When I can't even understand the opening paragraphs, I know to head elsewhere.  However, I DID find a perfect little app that does just what I want - Konserve.  Supposedly a KDE app, but it runs fine in my Gnome Ubuntu environment.  It provides easy to build GUI rules for making various backups that go to various places - I can pick one directory and back it up to another hard drive and an FTP site, and another directory and back it up to a different hard drive, with different time cycles between back ups for each item.  It's excellent.  Got it going right now making my first biz files backup.  :)

Thanks for the help, folks!  I'm sorry most of the suggestions went over my head, but I'm learning as quick as I can.

---

### Post by ushills on 2007-11-02
> **TreverT said:**
> I looked at both, but they were way beyond my needs and way over my head.  When I can't even understand the opening paragraphs, I know to head elsewhere.  However, I DID find a perfect little app that does just what I want - Konserve.  Supposedly a KDE app, but it runs fine in my Gnome Ubuntu environment.  It provides easy to build GUI rules for making various backups that go to various places - I can pick one directory and back it up to another hard drive and an FTP site, and another directory and back it up to a different hard drive, with different time cycles between back ups for each item.  It's excellent.  Got it going right now making my first biz files backup.  :)

Thanks for the help, folks!  I'm sorry most of the suggestions went over my head, but I'm learning as quick as I can.

The only problem I would with just making a copy of a file is if that file is delected or corrupted then you make a backup of the corrupted file or it is deleted.  Backupninja although requiring some manual configuration can keep many days previous versions of files as incremental backups.

Reading is essential however you could modify the configuration files on my site, they are fairly slef-explanatory.

---

### Post by AndyCooll on 2007-11-02
> **Hospadar said:**
> If you just need to copy files to a certain location, and you are comfortable using the command line (or are willing to learn) you could use cron jobs (with the "crontab" and "cron" programs) to do regularly scheduled simple operations.

You'd want to do some reading into this, it's probably not the best solution if you want a system-restore type situation or a backup scheme more complex than just file copies.

Following on from this (and assuming your have no fear of the command line), rsync and the cron would be a good way to go. rsync is the tool that synchronises your folders, and cron is the "scheduler" and automates the process, i.e tells rsync to run at a certain time every hour/day/week etc depending on what you choose. Both apps are already installed.

:cool:

---

### Post by philinux on 2007-11-02
If you need a gui then Grsync is in synaptic

---

### Post by TreverT on 2007-11-02
> **ushills said:**
> The only problem I would with just making a copy of a file is if that file is delected or corrupted then you make a backup of the corrupted file or it is deleted.  Backupninja although requiring some manual configuration can keep many days previous versions of files as incremental backups.

Reading is essential however you could modify the configuration files on my site, they are fairly slef-explanatory.

Please DON'T think I'm knocking on your app or anything of the sort, I'm sure it's very capable.  But, my wife and I both tried hard reading through the instructions and they really were way beyond my level of Linux knowledge at the moment.  I'm currently in the "Just need to get the basic essentials running so I can get back to doing productive work" stage...  got something like twenty biz emails stacked up waiting for answers plus the need to close out last month.  So, learning complex new stuff is going to have to wait a bit, but I'll get there.

Regarding the incremental backups, though, Konserve handles that.  You can set a single backup profile to either continually rewrite the same file, or keep timestamped versions going back as far as you like, with auto-deletion of older files beginning whenever you want.

---

### Post by ushills on 2007-11-02
Don't think you are knocking at all:)

I too struggled to find a backup utility that suited my needs, that is the good thing about linux many different ways of doing things and free to try them all.

I must admit the lack of a GUI is an issue with backupninja especially when restoring historic files unless you understand rdiff-backup.

A quality GUI based incremental backup util that allows backup to DVD-RAM would fulfill my needs.

---

### Post by TreverT on 2007-11-02
> **ushills said:**
> Don't think you are knocking at all:)

I too struggled to find a backup utility that suited my needs, that is the good thing about linux many different ways of doing things and free to try them all.

I must admit the lack of a GUI is an issue with backupninja especially when restoring historic files unless you understand rdiff-backup.

A quality GUI based incremental backup util that allows backup to DVD-RAM would fulfill my needs.

Konserve will write the backup to anything on the system, supposedly.  I haven't tried writing anything to a DVD yet but I'd think it would work there, too.  You may want to have a look at it, it's a very capable little GUI setup and since you seem to be a very knowledgeable Linux guru, it's possible you could tweak it to your own needs?

---

