---
title: "[SOLVED] A backup program is wanted"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-08-06
Greetings.
In Windows I use a program which will backup and incrementally synchronize my folders to my usb hard drive.
I see that in Ubuntu there is a program called "Keep", but note that that program is for the KDE desktop.
Does that mean that it is not suitable for using in Gnome?
Is there a Gnome program I can get which will do the same job for me?
Regards
John

---

### Post by Cypher on 2007-08-06
KDE apps will run within Gnome without any issues. If you do install it, it will install the necessary KDE libs. If the app doesn't need anything specific from KDE to function/perform backup, then it should work fine in Gnome, give it a shot..

---

### Post by Andavane on 2007-08-06
Thank you.
Will it also maintain incremental backups?
Do you think I will still be able to keep backing up from Windows?
The reason I ask it that are reasons why I must operate in Windows XP from time to time.
Thank you.
John

---

### Post by Cypher on 2007-08-06
I personally haven't used it, so I can't tell you if it will keep incremental backups.

---

### Post by Inxsible on 2007-08-06
Yet another backup software is SBackup. But I am not sure if it supports incremental backups.

---

### Post by dpar on 2007-08-06
From the sbackup wiki......

Feature list (v0.9)

    * Backup any subset of files and directories
    * Exclude files and directories by regex expressions
    * Exclude files by type (extension)
    * Exclude files by maximum file size
    * Backup to local filesystem
    * Backup to any Gnome-VFS supported remote filesystem (including sftp and ftp)
    * Full and incremental backups
    * Scheduling backups via cron
    * Gnome GUI for configuration
    * Gnome GUI for restore
    * Command-line restore tool that also provides a Python API for restoring a file or directory
    * Backing up package list in Debian derived distributions
    * On restore, existing files are not overwritten, but are renamed to a safe name

---

### Post by por100pre1 on 2007-08-06
> **Andavane said:**
> Greetings.
In Windows I use a program which will backup and incrementally synchronize my folders to my usb hard drive.
I see that in Ubuntu there is a program called "Keep", but note that that program is for the KDE desktop.
Does that mean that it is not suitable for using in Gnome?
Is there a Gnome program I can get which will do the same job for me?
Regards
John

Use Grsync. It does the job on my PC with external HDD. Hope it helps you. :)

---

### Post by Inxsible on 2007-08-06
> **dpar said:**
> From the sbackup wiki......

Feature list (v0.9)

    * Backup any subset of files and directories
    * Exclude files and directories by regex expressions
    * Exclude files by type (extension)
    * Exclude files by maximum file size
    * Backup to local filesystem
    * Backup to any Gnome-VFS supported remote filesystem (including sftp and ftp)
    * [COLOR=Red]Full and incremental backups[/COLOR]
    * Scheduling backups via cron
    * Gnome GUI for configuration
    * Gnome GUI for restore
    * Command-line restore tool that also provides a Python API for restoring a file or directory
    * Backing up package list in Debian derived distributions
    * On restore, existing files are not overwritten, but are renamed to a safe name
Thanks for the clarification dpar !! :)

---

### Post by Andavane on 2007-08-14
> **por100pre1 said:**
> Use Grsync. It does the job on my PC with external HDD. Hope it helps you. :)
Thanks very much.
errr... How exactly do I get 'Grsync' ?
Regards
John

---

### Post by forestpixie on 2007-08-14
> **Andavane said:**
> Thanks very much.
errr... How exactly do I get 'Grsync' ?
Regards
John

you can install from synaptic or apt-get

---

### Post by Andavane on 2007-08-14
> **forestpixie said:**
> you can install from synaptic or apt-get

I found synaptic package manager but could not see "Grsync" in there.
Sorry, I am not sure what apt-get is... ;)
can you clarify more?
Regards
John

---

### Post by mcurtiss1970 on 2007-08-14
there's also [http://www.jungledisk.com/download.shtml](http://www.jungledisk.com/download.shtml) .  it's a pay site using amazon.com's storage, and it has a linux client for download.

---

### Post by DugieHowsa on 2007-08-14
I use the JetS3t toolkit.  Its java, so it runs on any platform.  It may not be as full features as some of the other tools, but it does the job for me.  Like jungledisk, it also utilizes the Amazon S3 service.  I am able to back up all my data for pennies a month.

Here is a write up I made on installing and running JetS3t:
[http://ubuntuforums.org/showthread.php?t=524811](http://ubuntuforums.org/showthread.php?t=524811)

Here is where you can find more info on Amazon S3:
[http://www.amazon.com/s3](http://www.amazon.com/s3)

---

### Post by quinnten83 on 2007-08-14
I just recently started using unison. This is more of a synchronisation program which I use to sync my homefolders on several computers.
It has a sort of incremental system, perhaps it will work.
 someone on this forum once gave me this link

[http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually]("http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually")
it has good information on software installation in Ubuntu.

---

### Post by nichipet on 2007-08-14
> **Andavane said:**
> I found synaptic package manager but could not see "Grsync" in there.
Sorry, I am not sure what apt-get is... ;)
can you clarify more?
Regards
John

Hm.. I see grsync in my Synaptic. You probably don't have the universe repository enabled. Go into Synaptic (System:Administration:Synaptic Package Manager), then go to Settings:Repositories. In what should be the first screen, Ubuntu Software, there is a checkbox next to Community-maintained Open Source software (universe). Make sure the box has a check mark, close the window, then click Reload. Search for grsync and it should come up. If it doesn't, go into Applications:Accessories:Terminal and give us the output of:

```
cat /etc/apt/sources.list
```

---

### Post by Andavane on 2007-08-14
Yes, thank you, chaps.
I now realise how to get a program out of "synaptic":
It was just a matter of clicking on "search", and then typing in the name ;)
It's always easy when you see how to doit.
Well that's another thing learned for today!
Thanks again one and all
Regards
John

---

### Post by dj1120 on 2007-09-03
Thanks You answered my question about full backups with out me asking!! I used grsync to my external HD it works great!!

---

### Post by Andavane on 2007-09-03
Jolly Good!
Another problem solved ;)
Regards
John

---

