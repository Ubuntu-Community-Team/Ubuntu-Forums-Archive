---
title: "Backing up the system"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-05-06
How do you do a system backup for Ubuntu (I'm using 7.04 Feisty Fawn, both Gnome and KDE desktops installed). I copy my main files onto a hard disk, but I don't know how to backup the system settings so every time something goes wrong I have to re-download all the programmes I was using. What is a backup system recommended by the Ubuntu community to save the packages and other system settings??

---

### Post by aysiu on 2007-05-06
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by hyper_ch on 2007-05-06
I have written my own little shell script to do backups using rsync and hardlinks :)

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=woN1pdW
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

Then here my list of excluded directories:
backup_exclude
```

/backup/
/bin/
/boot/
/cdrom/
/dev/
/home/hyper/vmware/
/home/hyper/Exchange/OTR/
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

and here my cron job:
```

# Backup
0 3,9,15,21 * * * sh /backup/backup.sh

```

that should backup all important things... you may want to alter that to your needs...

I don't backup the /media folder because my backup harddisk is in there.... I just symlinked /backup to /media/sdb1

---

### Post by FerGeCo on 2007-05-06
nice script.
only thing i had to do was create an 'old' directory in the /backup directory.

---

### Post by hyper_ch on 2007-05-06
thx for pointing this out :) I'll alter my script so that it also attempts to create the "old" folder :)

---

### Post by FerGeCo on 2007-05-06
No problem (:

Just another thing: Your script copies all the files to the old/$NOW directory but it doesn't copy the sql databases .. is this by design ?

And i'm thinking of putting a mail thinggie at the end so the backup result will be mailed to me ..
I hope you don't mind if i alter it a little.

---

### Post by hyper_ch on 2007-05-06
Well, it does backup the mysql files :)

(1) It createds a new "old" folder (just mk)
(2) It dumps the mysql-dbs into /mysql_backup
(3) It syncs your files with the $current folder
(4) It hardlinks the $current to old/$now

(Furthermore you also have the orginial mysql backup files in /var/lib/mysql --> but when they are being access by mysql and by the filesystem the backup may become corrupt... hence I also make a dump of those dbs)

Go ahead with improvements... I published this here a long time ago on howtoforge and improvments are welcomed :)

[on Howtoforge I even added how to make remote backups by using rsync over SSH]

---

### Post by hyper_ch on 2007-05-06
So, I added now that auto-removal of old backups after a certain amount of days :)

---

### Post by kevinp on 2007-05-24
Also check out this cool program that uses the hard link feature of rsync but manages the resulting output folders well:

Link-Backup
[http://www.scottlu.com/Content/Link-Backup.html](http://www.scottlu.com/Content/Link-Backup.html)

---

