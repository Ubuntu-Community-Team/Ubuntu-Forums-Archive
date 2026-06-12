---
title: "Ubuntu 'system restore point' alternative?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by jakelee on 2007-12-18
Hey all, first time poster here.

From searching around, it would appear that there is no (yet?) simple way to create some sort of system restore point ala Windows XP.  That's fine, but I imagine there is likely some other way to create a similar effect without a major hassle?

In a Ubuntu book I've been reading, the author states that you can save yourself from yourself via the initial boot window where you should be able to select from multiple Ubuntu 'installs', simply choosing a lowered number (older date?) than the normal one.

However, after borking up my system multiple times in multiple ways, I always see only the the 2 options, 'generic' and whatever the 'safe mode', 'recovery mode', etc...is called. If this worked the way it was described in the book, than I probably wouldn't be posting this!

Anyway, so here I am back to the point where I have everything setup exactly as I like it, and I'm eager to get back to further experimenting which will more than likely result in various things getting broken (again).  Perfect time to figure out how to best save this current state the best I can...

Ideally this would encompass nasty problems that can come about after screwing up system permissions/ownership...not that I've ever done that personally :::cough:::  :)
Maybe too much to hope for though?

Next best thing would be some semi-convenient way to just revert the entire Ubuntu install back to square 1, or maybe square-2,...all freshly installed with devices detected and configured, with all default settings and everything across the board?  i.e. too impatient to nuke the entire thing and re-install fully from scratch (via CD).

Suggestions?

Thanks much in advance!

---

### Post by philinux on 2007-12-18
I'd settle for an undo button. :lolflag:

---

### Post by skyjacker on 2007-12-18
> **philinux said:**
> I'd settle for an undo button. :lolflag:
+1

---

### Post by Niniel on 2007-12-18
You sound like you need to pull a disk image of your current system and then play that back once you screwed up your installation again. :)

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page") 

[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by thelatinist on 2007-12-18
I suggest backing everything up using tar.  You can then restore it using a simple command to overwrite your entire system with the backup, all while Ubuntu is running.

More information can be found on this topic at [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087).

I have created a script I use to automate the process which backs up my root and home separately and saves them in separate folders, with date-and-time stamps in filenames.  That way I can easily determine which file to use to restore my system to whatever state I want.

If you are interested, the script is:

```
#!/bin/sh

PATH=/usr/ucb:/usr/bin:/bin; export PATH

##################################################################################################
#                          The following variables may be defined below:                         #
#                                                                                                #
# BACKUP_LOCATION is the folder where backups should be saved; the default is /Backup            #
# ROOT_TIME is the length of time, in days, to preserve backups of /; the default is 90 days     #
# ROOT_TIME is the length of time, in days, to preserve backups of /home; the default is 90 days #
##################################################################################################

# Variables

BACKUP_LOCATION=/Backup
ROOT_TIME=90
HOME_TIME=90

# Export the variables set in the previous section

export BACKUP_LOCATION; export ROOT_TIME; export HOME_Time

# Tar and gzip the folder /; exclude unnecessary folders such as /proc /lost+found /mnt /media /sys; exclude /home

tar cvpzf $BACKUP_LOCATION/Root/Backup-$(date +"%b-%d-%y-%T").tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/media --exclude=/sys --exclude=/home /

# Tar and gzip the folder /home; if you wish to exclude subdirectories, add the switch --exclude=/your_directory.

tar cvpzf $BACKUP_LOCATION/Home/Home-Backup-$(date +"%b-%d-%y-%T").tgz --exclude= /home

# Delete backups older than the time specified in the variables section, then exit

find $BACKUP_LOCATION/Root/*.tgz -mtime +$ROOT_TIME -exec rm {} \;

find $BACKUP_LOCATION/Home/*.tgz -mtime +$HOME_TIME -exec rm {} \;

exit
```

To restore from one of these backups, you simply cd to the directory containing the file you are trying to restore and use

```
sudo tar xvpzf *filename* -C /
```

to restore root or

```
sudo tar xvpzf *filename* -C /home
```

to restore home (replacing *filename* with the name of the backup file).

---

### Post by cub682 on 2007-12-18
I use Remastersys, works great.

[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

---

