---
title: "I've never performed a backup before"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-12-29
Hey folks . . .I've never had to perform a backup before, but I'd like to get in the habit of doing so . . .I have a lot of stored data on my machine, mostly in media form . . .
The reason I want to start backing things up is because I am interested in turning this machine into a toy for tweaking and adding new programs to. Do I have to waste all the CDs I own to save my computer from losing everything if I mess up? I don't want to use several CDs for each back up I perform.

---

### Post by evilghost on 2006-12-29
Get an external hard drive and backup to it.

---

### Post by optotron on 2006-12-29
Do you have another machine to backup the files to?

I like the rdiff-backup program, you can use it to back up to a remote computer via ssh-connection, and the thing about rdiff is that it only backup files that've changed, and also saves all the different versions of each document

!

---

### Post by hyper_ch on 2006-12-29
if you also make use of hardlinks and rdiff or rsync or a similar program you can make incremental snapshot-style backups.
That means:
incremental: Only altered data will be transferred (makes backup time quicker except for the first time)
snapshot-style: you have a complete backup at a given time (due to hardlinks)

I make a backup every 6h to another disk in my computer (and also upload parts of it to my webserver through SSH)

---

### Post by moshuptrail on 2006-12-29
I was reading the responses and thinking - an external HD, good idea. Then I thought, why not an internal HD?  Well, if you're talking about a laptop, that would be a problem, wouldn't it? But, if you have a desktop with an extra slot, why not an internal HD?

More importantly, the media you choose will depend on your current system, and the quantity of data to back up.  I just backed up all my music files and photos to a bunch of CDs.  It was cheap.  Cost me $7.50 for 50 CD's and I used about half of them.  It's not like those files will ever be changed, so I only have to do it once.  (kind of a manual rdiff)

I have a bunch of active documents (stuff that does change) in a "My Documents" type folder and I back them up to a 1G memory stick now and again.  Keep it simple I say.

---

### Post by hyper_ch on 2006-12-29
answer for not (only) an external drive is simple:

Just imagine you do a stupid thing or someone hacks into your computer and deletes all of it....  it's gone... hence you need some backup away from that computer... for me I do put it on my webserver that's a few hundert kilometers aways....

CDs is good but it takes ages....

with rdiff or rsync you just plugin your usb drive and let a script do the magic... no need to select what you want to backup and and and....

Here's my small little thing:

backup.sh
> 
#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=woN1pdW
MYSQLHOST=localhost
MYSQLBACKUPDIR=/mysql_backup
EXCLUDES=/root/backup_exclude        # File containing exludes

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

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING CURRENT DATE / TIME
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
MKDIR=$BACKUPDIR/$NOW/
$MK $MKDIR

# CREATE MYSQL BACKUP
# Remove existing backup dir
$RM -Rf $MYSQLBACKUPDIR

# Create new backup dir
$MK $MYSQLBACKUPDIR

#Dump new files
#for i in $(echo 'SHOW DATABASES;' | $MYSQL -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST|$GREP -v '^Database$'); do
#  $MYSQLDUMP                                                    \
#  -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST                         \
#  -Q -c -C --add-drop-table --add-locks --quick --lock-tables   \
#  $i > $MYSQLBACKUPDIR/$i.sql;
#done;

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


backup_exclude
> 
/backup/
/bin/
/boot/
/cdrom/
/dev/
/initrd/
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
/var/cache/
/var/log/
/var/spool/
/var/lib/
/var/lib/php4/
/var/lib/mysql/

I exclude the /backup folder and the /media folder as I don't want any recurring things

and finally I let a cron handle all of that:
> 
# Backup
0 3,9,15,21 * * * sh /root/backup.sh


---

### Post by CheshireMac on 2006-12-29
Alright . . .I have a thought . . .I have two physical hard drives on my machine . . .one is only for storage, where the other is for system files . . .if I were to move my backup to the storage drive, would it be damaged by a screw up in the main drive? All I have on the storage drive is media . . .

---

### Post by hyper_ch on 2006-12-29
no, a screw up in the main drive shouldn't affect the backup drive at all... however there is still the danger of you mistakenly delete everything or a hacker... or maybe a fire in your apartment that renders the backup drive also useless... safest thing is to have decentralized backups...
But making backups on another drive is a lot safer than not making backups at all...
Additionally you could take my scripts above as starting point and have the drive mounted when you do a backup and afterwards unmount it again...

---

### Post by T_Jonsson on 2006-12-29
The media you store your backups on depends on how importent the information is. Is't only some funny mails you like you can use a CD. But since the life time of a cd, especialy the cheap ones, are short you are better of using harddrives for more important stuff. 

Is the information vital for you it should be backup and stored in a remote location (think fire and you may guess why). There are many free online-backup services that meets the needs of a private person.

---

