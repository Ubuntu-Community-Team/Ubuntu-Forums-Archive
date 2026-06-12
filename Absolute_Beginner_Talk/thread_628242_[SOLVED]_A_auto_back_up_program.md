---
title: "[SOLVED] A auto back up program"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Bob_12 on 2007-12-01
Is there a good program for Ubuntu that will automatically back up files/folders to a location of my choosing? Thanks for all the help!

---

### Post by mikeyphi on 2007-12-01
> **Bob_12 said:**
> Is there a good program for Ubuntu that will automatically back up files/folders to a location of my choosing? Thanks for all the help!

Have a look at Simple Backup (sbackup) available through Synaptic.

---

### Post by aridus on 2007-12-01
I have done a lot of research on this over the last week and installed and tried a variety of tools both simple and complicated. My conclusion for now is that if, like me, you can't manage the complication of a command line programme, sbackup (in synaptic) is the best available at the moment for simple backups to an external drive, but that in the future two Apple TimeMachine type progs may be better. I have tried them both but neither are fully developed yet: TimeVault ([https://wiki.ubuntu.com/TimeVault?highlight=%28timevault%29](https://wiki.ubuntu.com/TimeVault?highlight=%28timevault%29)) and FlyBack ([http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)). The two best command line backup programs seem to be rdiff-backup and rsnapshot (with perhaps the former having the edge as it backs up parts of files incrementally). If rdiff-backup had a nice front end I think it would be perfect (for me).

Martin

---

### Post by aridus on 2007-12-01
Something very useful that I just picked up in another thread ([http://ubuntuforums.org/showthread.php?t=628242](http://ubuntuforums.org/showthread.php?t=628242)). If you use an external USB drive for backing up and it is FAT32 your file size limit is 4 GB, which will probably not be enough. I am now going to format my USB drive as ext3 to avoid this problem.

Apparently the max size of a single file on ext3 depends on the block size (see [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)) but I don't know how to determine the block size (or to set it).  Anybody got any ideas?

---

### Post by kevinatkins on 2007-12-01
I use BackupPc, which is available from the repositories. This is quite a heavy-duty program, consisting of a server which is configured to back up multiple PC's. Once set up (it's not too difficult), operation is fully automatic and I've got it backing up to an external USB hard drive. It works very well indeed.

---

### Post by aridus on 2007-12-01
I tried to do this but couldn't figure it out. You say it is not too difficult to set up to back up to an external usb drive. Would you be able to provide a step-by-step guide to the basics of doing this?

thanks!

M

---

### Post by Bob_12 on 2007-12-01
Simple Back Up is great! Thanks so much for the help!

---

### Post by kevinatkins on 2007-12-02
Hi Aridus,

I don't think this thread is the right place to do a full step-by-step for BackupPC; the link below will take you to a pretty good how-to -

[http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc)

As regards using an external USB drive, what I did was make sure that the drive was formatted as Ext3 (NOT FAT, which is normally the default if you purchase an external hard drive) and adjust /etc/fstab to ensure that the drive is always mounted on boot..

If you run into problems, start a new thread and we'll take it from there.

Kevin.

---

### Post by aridus on 2007-12-02
OK, many thanks. I am looking at the tutorial.

Martin

---

