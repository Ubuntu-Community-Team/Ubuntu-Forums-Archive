---
title: "backup utility for Ubuntu"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-20
is there a backup utility in Ubuntu 7.10 that allows you to backup the entire contents of your hard disk (data only) that would be the equivalent to Norton Ghost?  i'm looking for something that will allow me to restore these backups to another hard disk say if my current hard drive crashes due to a hardware issue.  thanks.

---

### Post by reckless2k2 on 2008-01-20
a lot of people will tell you rsync.

---

### Post by FuturePilot on 2008-01-20
Partimage is good for this kind of thing
[http://www.partimage.org/Main_Page]("http://www.partimage.org/Main_Page")

---

### Post by erfahren on 2008-01-20
[sbackup](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html#more-5)

---

### Post by arsenic23 on 2008-01-20
I use the [Acronis]("http://www.acronis.com/") boot disc any time I need to back up an entire disk or partition.  Works good for any OS/filesystem.

---

### Post by rosegarden78 on 2008-01-20
A forensic computer specialist may suggest using the dd command from the terminal.  I believe a simple command similar to this

[Hypothetical command - do not use]
dd if="~/*" of="/media/yourUSBdrive"

creates a data dump of your home folder to your backup device.  Replace "~" with "/" and you will data dump your entire hard drive.  I can't go into the details of forensic analysis with dd command but I'm positive you can find more information.  One can even use dd command to data dump the boot sectors.

---

### Post by jon_gunnar on 2008-01-21
> **erfahren said:**
> [sbackup](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html#more-5)

Thanks for this.Iv really been thinking about backups for a long time and really found it a little strange that Ubuntu does not ship with a ready one installe.

---

### Post by philinux on 2008-01-21
Grsync

Is a nice gui for rsync

---

### Post by exactopposite on 2008-01-21
i haven't tried this yet myself but it looks promising

[http://tinyurl.com/ywkzby](http://tinyurl.com/ywkzby)

---

### Post by Matt26 on 2008-01-21
i ran a custom backup in sbackup config and directed it to my external usb hard drive- when i ran the backup i didn't see any progress indicator for the backup (is there one available?), just a message saying a backup has started in the background- and the HDD light on my case was quite busy so i figured it was running.. i left it for awhile and came back and checked my usb drive after the HDD light was idle and found no files.. any ideas what i am doing wrong here?

---

### Post by Het Irv on 2008-01-21
I have found this to be a good program.  [QuickStart 6.0]("http://ubuntuforums.org/showthread.php?t=613462").  It only requires you to install Ubuntu.  After that you can install alot of plug-ins and restore system, home, and configuration files.

---

### Post by jon_gunnar on 2008-01-21
> **Matt26 said:**
> i ran a custom backup in sbackup config and directed it to my external usb hard drive- when i ran the backup i didn't see any progress indicator for the backup (is there one available?), just a message saying a backup has started in the background- and the HDD light on my case was quite busy so i figured it was running.. i left it for awhile and came back and checked my usb drive after the HDD light was idle and found no files.. any ideas what i am doing wrong here?

I found the same situation.It says it runs in the background,no progress.And when I tried to open the file after a long time it end's up with a dump of error msg.
Will have a new try to day.

---

