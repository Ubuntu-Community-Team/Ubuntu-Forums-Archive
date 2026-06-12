---
title: "Auto-backup options"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Redbeard09 on 2008-03-04
Tried doing a search, but didn't turn up much.

I'm looking for a way to auto-backup various folders that include work and school projects to an external hard-drive.
Any help would be much appreciated.

---

### Post by hyper_ch on 2008-03-04
simplest thing would be to use rsync and setup a cron job to do the task in regular intervals.

I wrote myself a little shell script that does that and it uses hardlinks to create "snapshots". Meaning you'll have a full "backup" for dating xxx days back (but it won't use too much diskspace because of hardlinks).

The only questions are:

(1) is that external drive always connected

(2) if not, is it always connected at a given time so a scheduled backup can be made

(3) do you wish to perform manual backups?

---

### Post by Redbeard09 on 2008-03-04
It won't always be connected. I don't really have a need to manually back up anything else. This is mainly a work/paper writing machine and there isn't a lot of other files on here.

---

### Post by hyper_ch on 2008-03-04
well, you can write a shell script and run that manually... but if the drive isn't always connected when a backup is scheduled it's not really of much us then...

---

### Post by Redbeard09 on 2008-03-04
Ok, lets say I make an effort to keep it plugged in. How would I go about writing the script for this action?

---

### Post by kpkeerthi on 2008-03-04
You may want to check this out.
[http://ubuntuforums.org/showthread.php?t=187894](http://ubuntuforums.org/showthread.php?t=187894)

---

### Post by hyper_ch on 2008-03-04
I use my script

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=************
MYSQLPWD=*************
MYSQLHOST=localhost
MYSQLBACKUPDIR=/mysql_backup
EXCLUDES=/backup/backup_exclude        # File containing exludes
DAYS=90         # After how many days shall the backups be deleted?

# PATH VARIABLES
CP=/bin/cp;
MK=/bin/mkdir;
DATE=/bin/date;
RM=/bin/rm;
GREP=/bin/grep;
MYSQL=/usr/bin/mysql;
MYSQLDUMP=/usr/bin/mysqldump;
RSYNC=/usr/bin/rsync;
TOUCH=/bin/touch;
FIND=/usr/bin/find;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING CURRENT DATE / TIME
$MK $BACKUPDIR/current
$MK $BACKUPDIR/old
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
MKDIR=$BACKUPDIR/old/$NOW/
$MK $MKDIR

# CREATE MYSQL BACKUP
# Remove existing backup dir
$RM -Rf $MYSQLBACKUPDIR

# Create new backup dir
$MK $MYSQLBACKUPDIR

#Dump new files
for i in $(echo 'SHOW DATABASES;' | $MYSQL -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST|$GREP -v '^Database$'); do
  $MYSQLDUMP                                                    \
  -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST                         \
  -Q -c -C --add-drop-table --add-locks --quick --lock-tables   \
  $i > $MYSQLBACKUPDIR/$i.sql;
done;

# RUN RSYNC INTO CURRENT
$RSYNC                                                          \
        -avzp --delete --delete-excluded                        \
        --exclude-from="$EXCLUDES"                              \
        /                                                       \
        /$BACKUPDIR/current ;

# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current

# MAKE HARDLINK COPY
$CP -al $BACKUPDIR/current/* $MKDIR

# REMOVE OLD BACKUPS
for file in "$( $FIND $BACKUPDIR/old/ -maxdepth 1 -type d -mtime +$DAYS )"
do
  $RM -Rf $file
done

exit 0

```

backup_exclude
```

/backup/
/bin/
/boot/
/cdrom/
/dev/
/home/hyper/vmware/
/home/hyper/Exchange/OTR/
/home/hyper/B5/
/initrd/
/initrd.img
/ionitrd.img.old
/lib/
/lost+found/
/media/
/mnt/
/opt/
/proc/
/sbin/
/srv/
/sys/
/tmp/
/usr/
/var/backups/
/var/cache/
/var/crash/
/var/local/
/var/lock/
/var/opt/
/var/run/
/var/spool/
/var/tmp/

```

It will keep older backups for 90 days and then delete them. Because I use hardlinks it will not add much more disk space used for those older ones.

The whole mysql section can be cleared from that script (I doubt you need it).

And instead of using a --backup-exclude list you probably want to use a --backup-include list.

---

### Post by eldragon on 2008-03-04
there are already dozen of scripts that use rsync to do incremental backups.


i found the easiest of them all is called rsnapshot. search the repositories.

its quite easy to setup, and you can setup different backup schedules for different folders. and you can even run it manually (not recommended)

only thing thats lacking is email when there is a problem.....if i ever learn to script, i'll add the feature ;)

---

