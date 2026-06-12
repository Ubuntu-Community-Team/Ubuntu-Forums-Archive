---
title: "Shell script for backuping personal files"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Degeim on 2007-04-16
Hi!

I wan't a shell script (if that's the name; a .sh-file) that can backup my personal files.

I have two computers and a memory stick. One computer is Windows, and there I've made a program that can
 a) Save directories - one on the computer, and one on the memory stick - and compare files
 b) Inform me about how many files that are newer on one of them
 c) Let me press "Synchronize" and then copy the newer of two files and replace the older.

 - And that way I always have a backup of my newest personal files on both windows-computer and memory stick.

But I want to include my Linux-computer too, and I think a .sh-file is the best soulution for me. I have made quite a few scripts before, but never anything about files.

So I was wondering if anyone could supply me with scripts for the following:
 a) Compare two directories and tell me how many files that are changes.
 b) Let me copy synchronize the directories if I want to, and report that everything was done successfully (if it was, of course).

Thank you,
Degeim

---

### Post by jvc26 on 2007-04-16
Could you not just use a ready made solution like [rsync]("http://samba.anu.edu.au/rsync/") for your linux pc between the two directories?
Il

---

### Post by Degeim on 2007-04-16
Yes, I could. Thank you.

But I couldn't make that work either.

Could someone supply me with rsync-commands for synchronizing two directories in such a way that only the changed files are copied?


Thanks,
Degeim

---

### Post by aysiu on 2007-04-16
This is the one I use: ```
#!/bin/bash
rsync -av /original/directory /backup/directory
```

---

### Post by Degeim on 2007-04-16
Thank you!


I see the -v is for verbose, and the a is for archive (or -rlptgoD), but what exactly does -a do?

---

### Post by Degeim on 2007-04-17
OK, nevermind about that. It works, and then I'm happy.

But, I found I cannot use this. Of some strange reason, both my Windows and Linux backups the entire directory each time the other have touched the files, as if everything was older

Do they not use the same system for saving "Last changed"-dates?

Thanks,
Degeim

---

### Post by hyper_ch on 2007-04-17
rsync compares the file content and will only transmit the altered parts...

Can you post what command you tried?

I use this little script here

```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=************
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
MKDIR=$BACKUPDIR/old/$NOW/
$MK $BACKUPDIR/current
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

```

and here my exclude file:

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
/var/lib/
/var/local/
/var/lock/
/var/opt/
/var/run/
/var/spool/
/var/tmp/

```

I let this run every 6h :)

---

### Post by Degeim on 2007-04-17
Im running:
```
#!/bin/bash
rsync -av /original/directory /backup/directory
```

And it seems to [copy/alter] only the changed files, but it doesn't cooperate with Windows.

Windows thinks files Linux wrote today is older than Windows-files from yesterday and vice versa.

---

### Post by aysiu on 2007-04-17
Yes, *rsync* won't work for NTFS or FAT32 filesystems.

It works on Ext3 and HFS+ (and others, too)

---

### Post by Degeim on 2007-04-17
Pity. I really liked it.

But then I'm back to square one: is there any posibilities to make a shell script to do the job?

---

### Post by hyper_ch on 2007-04-18
well, rsync works on ntfs if windows is started and if you have cygwin installed... then you can also install within windows an rsync server... and that one works fine... I have such a setup at my mom's home.

---

