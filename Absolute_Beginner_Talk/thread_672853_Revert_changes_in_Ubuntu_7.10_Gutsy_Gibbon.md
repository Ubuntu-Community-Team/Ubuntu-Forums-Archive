---
title: "Revert changes in Ubuntu 7.10 Gutsy Gibbon"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by yogatta on 2008-01-20
I wonder if there is any way i could revert all changes and upgrades i made 
in my gutsy gibbon and make it fresh as after new installation? Like windows, 
they have System Restore that can restore back windows to early desired state.
is there any in ubuntu?

---

### Post by mathnerd314 on 2008-01-20
I guess you could just copy all your files to an external disk and reinstall Ubuntu... is that what you're asking?

---

### Post by Arthur Archnix on 2008-01-20
No.

If you upgraded from Feisty to Gutsy, there is no way to revert back to Feisty. If you upgrade a single program, you can uninstall that program using apt-get remove --purge PROGRAM_NAME, and then reinstall the old program.

---

### Post by yogatta on 2008-01-21
> **Arthur Archnix said:**
> No.

If you upgraded from Feisty to Gutsy, there is no way to revert back to Feisty. If you upgrade a single program, you can uninstall that program using apt-get remove --purge PROGRAM_NAME, and then reinstall the old program.

actually, what i mean is return back my gutsy gibbon after 2 weeks of use (added with upgrades and installation) into 2 weeks before (early state without installation and upgrades a.k.a. fresh installation from ubuntu CD).  Unlike windows, they have system restore. Do i make my self clear? the question is, is there any way to do this trick in ubuntu gutsy gibbon?

---

### Post by Arthur Archnix on 2008-01-21
As far as I know, no. There's no roll-back like in Windows, or Time Vault like on a Mac. From a fresh install there'd really be no point, it would likely take as long to restore as it would to do a clean install. There are back-up and restore options though. You'll find many threads on the forums about rsync, scheduling backups with cronjobs, etc.

The method I find easiest is to create before the install four partitions. One 7.5 GB ext3 at the start of the drive, a 1GB swap right after that, a 9 GB ext2 partition at the end of the drive mounted at /backups, and the rest just formatted to ext3 and mounted to /data. 

My root and home get installed to the 7.5GB / partition at the start. I put all my data (pictures, music, files, videos) on the largest partition mounted at /data. Once I have setup my computer to the way I like it, and installed the latest updates, I take out a program called PING (Ping is not ghost) and create a backup image of my drive and save it to the last partition (9GB). I call that backup Clean Install. Then about once a month, or every two weeks, I create a new image of my / saved to /backups and called Latest. It takes about 10 minutes to backup the drive. If ever I need to restore, I put the cd in the drive and restore from the backup partition. It takes about 10 minutes as well. 

Ping also gives you the option of creating a bootable dvd that you can use to just drop in and restore your computer.

Other options are available, other than this. But I don't know much about them since I've found a way that works for me. Have a glance around the forums though and you may find one that works for you as well.

---

