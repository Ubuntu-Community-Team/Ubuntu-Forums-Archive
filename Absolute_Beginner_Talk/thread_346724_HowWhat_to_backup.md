---
title: "How/What to backup?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-01-26
Hi,

Over the years, I've had enough harddrive failures that I've become totally paranoid about backups.  On my Windows PC, I use Norton Ghost, so that I can have a daily backup of my entire system, and can restore either the whole drive or any individual files - I know this is a bit of overkill, but it's saved my bacon a few times.

My question: What's the best way to handle Ubuntu backups?  I'm guessing that if I regularly save the users' home directories to a USB drive, that will protect essential stuff like emails, address books, etc.

I know that if I manage to totally break Ubuntu I can always reinstall from scratch, then get the users' essential files from this backup - but then I'd have to redo all my customisations, reinstall all sorts of stuff etc...  Is there Ubuntu software for making (and restoring!!) a complete drive image?

I'd be really interested to know how Ubuntu users deal with backups.

Thanks!

---

### Post by hyper_ch on 2007-01-26
I use rsync and the power of hardlinks to create every 6 hour an incremental snapshot-like backup on my "spare" harddisk and once a day I upload it to my "backup-server"... all done automatically :)

---

### Post by cudjoe on 2007-01-26
You can use Mondo to make live backup.
It will create ISO files, with all kind of support / destinations.

I use the wizard with command-line, which is very straightforward :

sudo mondoarchive

---

### Post by whitefort on 2007-01-26
Thanks guys.  rsinc and mondo.  I'll check them out.

I'm still trying to decide on a backup strategy for my Ubuntu machine. 

Mondo sounds like it might be good for occasional use, and maybe rsinc for daily backups of important files?

I'm thinking of getting a USB hard drive for the Ubuntu machine and using it for my backups...

Anyway, I'll check out rsinc and mondo.  Thanks!

---

### Post by highneko on 2007-01-26
I used [http://www.sysresccd.org/](http://www.sysresccd.org/) and liked it, but I have never had to restore the backup so don't know if that would go well. You would have to know how to mount and stuff like that. 

All I had to do was:
mkdir /extra
mount /dev/hda3 /extra
partimage

---

### Post by RudolfMDLT on 2007-01-26
You could just zip the entire system. It works quite well actually.

Pick a folder where you want to backup to, eg, /Backup then just exclude it from the backup.

sudo tar cvpzf /backup/backup.tgz  --exclude=/mnt --exclude=/sys --exclude=/windrives --exclude=/[COLOR="Yellow"]XXX[/COLOR] /

where XXX is any other folders or drives you have mounted and don't want backedup. 

When you do crash the machine just re-install ubuntu and untar the file using sudo.

Cheers,

Rudolf

---

### Post by hyper_ch on 2007-01-26
Here's how I do it:

(1) Get rsync
```

sudo apt-get install rsync

```

(2) Create a symlink (I just think that makes it easier)
```

ln -s /media/BACKUP_DRIVE /backup

```
If your USB drive is mounted at /media/sdb1 then use this:
```

ln -s /media/sdb1 /backup

```
That way you will have a /backup folder that points to your usb-drive or to some drive... if you decide making backups to some other drive you just modify the symlink to point somewhere else instead of being required to alter the shell scripts....

(3) Create the backup shell script
backup.sh
```

sudo nano /root/backup.sh

```
or you can use this:
```

gksudo kate /root/backup.sh

```
or open the backup.sh file in /root with some other text editor as root....

(4) Enter the backup code :)
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
EXCLUDES=/root/backup_exclude        # File containing exludes

# PATH VARIABLES
CP=/bin/cp;
MK=/bin/mkdir;
DATE=/bin/date;
RM=/bin/rm;
GREP=/bin/grep;
RSYNC=/usr/bin/rsync;
TOUCH=/bin/touch;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING NECESSARY FOLDERS
$MK $BACKUPDIR
CURRENT=$BACKUPDIR/current
OLD=$BACKUPDIR/old
$MK $CURRENT
$MK $OLD
# CREATING CURRENT DATE / TIME
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
NOW=$OLD/$NOW
$MK $NOW

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
Modify the vars in the "user variables section"

You can save the file in nano by pressing "ctrl-x", then "y" and then hit "enter"

(5) Create the backup_exclude file in /root (or wherever you have set it to)
```

sudo nano /root/backup_exlude

```
and add the dirs you want to have excluded
```

/backup/
/bin/
/boot/
/cdrom/
/dev/
/home/hyper/vmware/
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

```
Necessary to exclude the usb-drive (e.g. /media or /media/USB-DRIVE) and also the /backup one as you would enter a loop.....

(6) Create a cron job
```

sudo nano /root/cron.txt

```
Enter
```

# Backup
0 3,9,15,21 * * * sh /root/backup.sh

```
This will execute the backup script every six hours at 3am, 9am, 3 pm and 9pm....
Add the cronjob file to the crontab by issuing this command
```

sudo crontab /root/cron.txt

```
Test whether it was added by issuing this command:
```

sudo crontab -l

```

That's it :)

---

### Post by lamego on 2007-01-26
Please note that most of your customizations are probably kept on the users home dirs.

---

### Post by hyper_ch on 2007-01-26
the /etc folder is also important... there modifications on system services (daemons) will be stored :)

---

### Post by TheWizzard on 2007-01-26
the ultimate backup-guide:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

backing up both /home and /etc is sufficient

you can also make a list of installed software and use this list to install everything the way it was: 
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

### Post by phil90 on 2007-01-27
Hello


Is there a way for me to find out the purposes of the folders before I exclude it. So that I dont exclude folder that would be required. Like I know the dev folder contain information about the partition cdrom etc. So if I don't back it up when  I would restore would it not not restore the Superblock and the filesystem????

---

### Post by whitefort on 2007-01-27
Thanks for all the replies, everyone - much appreciated!

I'm gong to print a lot of this stuff out, so I can find it again when I need it!

---

### Post by lnxnewbie on 2007-01-27
I use Simple Backup Config/Restore
System->Administration->Simple Backup Config   (configure backup)
System->Administration->Simple Backup Restore (to restore old backup).

---

### Post by xfile087 on 2007-03-05
> **RudolfMDLT said:**
> You could just zip the entire system. It works quite well actually.

Pick a folder where you want to backup to, eg, /Backup then just exclude it from the backup.

sudo tar cvpzf /backup/backup.tgz  --exclude=/mnt --exclude=/sys --exclude=/windrives --exclude=/[COLOR="Yellow"]XXX[/COLOR] /

where XXX is any other folders or drives you have mounted and don't want backedup. 

When you do crash the machine just re-install ubuntu and untar the file using sudo.

Cheers,

Rudolf

Re-install? If it it's backup all you have to do it is boot from a Live CD, mount your hard drive and extract the archive? That is all I do for mine and it works perfectly! The only thing re-install may do is fix grub - but you can do that yourself.

---

