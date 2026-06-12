---
title: "Very simple backup procedure"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-10-17
Hi

Having once lost all my files by overwriting my Suse installation, I'm very keen to avoid a repeat with Ubuntu.

I've got an external hard disk, and I've been experimenting with archiving my personal folder to this drive using tar. Initially I tried the command line, and did OK, but I  then discovered I could archive a whole folder by simply right-clicking on the folder and selecting 'archive to'. By right-clicking on the tar file on the hard disk I can then select 'extract here' to re-create  the original folder - I think, complete with all my email stuff and browser bookmarks. However, I'm unclear as to whether this is a sensible basis for re-building my system in the event of, say, a hard disk crash.

If, in the event of a hard disk crash, could I rebuild my system by re-installing ubuntu, and then copying my home folder from the external drive into home?

Are there any advantages in using tar? Can't I just start by copying my home folder onto the hard disk?

Does anyone have any better ideas? This must be a fairly common problem.

All help and advice much appreciated.

Regards

Roger D

---

### Post by xyz on 2006-10-17
I have used these 2 howto's and have never had any pbms with restoring things to a working OS:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
Uses Live-CD...
AND
[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive](http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive)

The day I discovered backup procedures...my life got MUCH simpler!

Also this seems really interesting:
[http://www.ubuntuforums.org/showthread.php?t=240326](http://www.ubuntuforums.org/showthread.php?t=240326)


How To Backup A Ubuntu System with hourly, daily, and weekly backups.

---

### Post by RogerD on 2006-10-17
Many thanks

I was hoping to avoid the command line. The archive option from the mouse must be there for a reason. I've just trying to find out how to make the best use of it. I appreciate this approach may not be a flexible or as powerful as the command line and tar, but, as a beginner, I'm happy to live with that

Roger D

---

### Post by TheWizzard on 2006-10-17
write a script like this:

```
#!/bin/bash


# personal files
rsync -azv --numeric-ids --exclude '*/.thumbnails/' --exclude '*/Cache/' --exclude '*/Trash/' --exclude '*/Desktop/' --exclude '*/.beagle/' /home /media/sda/Backups/PC.bak

# computer settings
rsync -azv /etc /media/sda/Backups/PC.bak

```

make it executable and put it in one of the cron folders

you can also take a look at dirvish: 

from their website: 
> Dirvish is a fast, disk based, rotating network backup system.
With dirvish you can maintain a set of complete images of your filesystems with unattended creation and expiration. A dirvish backup vault is like a time machine for your data.

---

### Post by hyper_ch on 2006-10-17
If you want to have incremental snapshot-style backups I recommend rsync and the use of hardlinks.

---

