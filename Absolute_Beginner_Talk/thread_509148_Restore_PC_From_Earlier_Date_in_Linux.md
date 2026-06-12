---
title: "Restore PC From Earlier Date in Linux?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by bme on 2007-07-25
Is there a linux way of restoring the system to an earlier point? Similar to windows restore?

---

### Post by trent dillman on 2007-07-25
...

---

### Post by hyper_ch on 2007-07-25
Not by default... however backups and stuff can be easily made...

---

### Post by tomcheng76 on 2007-07-25
Try SBackup
[http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

---

### Post by paradoc on 2007-07-25
This might help?..Haven't needed to do it yet, but look into the cpio and dd utilities, (mentioned in the literature)if you want to take  regular file backups and return to them at a later date??

---

### Post by bme on 2007-07-25
the suggestion (I think) only backs up files and not the whole system.What I am asking is similar to windows backup in which when something does not work in windows I can restore form an earlier date to a working state.
I do a lot of experimenting in my ubuntu and sometimes I do something which result in an ubuntu that I don't like. It would be good thing if I can restore to an earlier date like before I installed a certain driver...

---

### Post by dan171717 on 2007-07-25
i think there is a backup and restore program in add/remove

---

### Post by hyper_ch on 2007-07-25
Well, I use my own little script which does make incremental snap-shot style backups of my data...

---

### Post by Jimmyfj on 2007-07-25
Well I use Time Vault for that - TimeVault is a project still in development so please remember that this is beta software. You'll find Timevault at this address:

[https://launchpad.net/timevault/+download](https://launchpad.net/timevault/+download)

---

### Post by ADT on 2007-07-25
Is it safe to do a copy:

```
sudo cp -v -p -r /bin /boot /dev /etc /lib .... /mnt/usb/backup/sys
```

as a form of backup

and then to cp all those directories back to / when something goes wrong?

If you couldnt login to your system then you could run a live cd and mount the usb drive from the live cd.
Then mount the hard drive partition containing ubuntu's / and then copy all the backup files to ubuntu's /.


Is this too messy. What GUI style program could do something like this?

---

### Post by bigken on 2007-07-25
> **Jimmyfj said:**
> Well I use Time Vault for that - TimeVault is a project still in development so please remember that this is beta software. You'll find Timevault at this address:

[https://launchpad.net/timevault/+download](https://launchpad.net/timevault/+download)

Just wondering is there a version or similar program for kubuntu

---

### Post by Jimmyfj on 2007-07-25
I know from the developer himself that he and a friend of his are working on a port for the default file manager in Kubuntu, Conqueror, I think it's called, but I don't know how far they are in this work - The link I gave in my previous input is where I imagine hell upload TimeVault for KDE. Or at least a link to the KDE version. I'll try to get hold of him and return with further info if possible.

---

### Post by bigken on 2007-07-25
> **Jimmyfj said:**
> I know from the developer himself that he and a friend of his are working on a port for the default file manager in Kubuntu, Conqueror, I think it's called, but I don't know how far they are in this work - The link I gave in my previous input is where I imagine hell upload TimeVault for KDE. Or at least a link to the KDE version. I'll try to get hold of him and return with further info if possible.

cheers ;)


I will keep an eye on the download site

---

### Post by ddrichardson on 2007-07-25
This hasn't been mentioned, but I like to make a disk image after everything is set the way I want - there's a [brilliant live cd]("http://www.sysresccd.org/Main_Page") that contains [partimage]("http://www.partimage.org/Main_Page").

This is a great way to try things out then be able to put everything back the way it was.

---

### Post by hyper_ch on 2007-07-25
ddrichardson:

I prefer to backup the config file and data files... and do a clean install and not making a disk image. In order to do a "quick" system restore I have written myself an install script which restores my sources.list, fetches all my normal applications, downloads and installs them and puts config files back. Then I'm at the point where I actually left but all applications are up-to-date.

---

### Post by Sbarton on 2007-07-25
Not sure if this is worth looking at 
[http://www.improvedsource.com/view.php/Linux-System/18](http://www.improvedsource.com/view.php/Linux-System/18)
regards

---

### Post by bme on 2007-08-07
> **hyper_ch said:**
> ddrichardson:

I prefer to backup the config file and data files... and do a clean install and not making a disk image. In order to do a "quick" system restore I have written myself an install script which restores my sources.list, fetches all my normal applications, downloads and installs them and puts config files back. Then I'm at the point where I actually left but all applications are up-to-date.

If you don't mind please share the script here? anyway this is a lot of work just to restore to a formerly working state,why download again something which is already there.....XP/Vista system restore is better in this regard.Perhaps another "project" for Linux programmers to think about,this system restore?

---

### Post by hyper_ch on 2007-08-07
Each one his own....
I don't like disk images as they use too much space. I do my backups with rsync and hardlinks... basically I have a full backup every 6h over a period of 90 days.

And re-setting up the system is quite easy... with my "install" script I do all the necessary modfications in there - this is the superiority of config files compared to a registry... you just reinstall the piece of software and replace the config file with your old modified one and it works the same as before.

---

### Post by eentonig on 2007-08-07
hyper_ch,

Do you mind sharing your script? I had a similar setup, but someone overwrote my usb where I kept the script.(stupid me for not having a backup for that.)

---

### Post by hyper_ch on 2007-08-07
It's actually two scripts and three files ;)

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=***********
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

install.sh
```

#!/bin/bash

################ RESTORE SOURCES.LIST ###############

cp -f backup_files/sources.list /etc/apt/sources.list
cp -f backup_files/secring.gpg /etc/apt/secring.gpg
cp -f backup_files/trustdb.gpg /etc/apt/trustdb.gpg
cp -f backup_files/trusted.gpg /etc/apt/trusted.gpg

#####################################################

aptitude -y remove mozilla-thunderbird

aptitude update
aptitude -y upgrade

# Skype
aptitude -y install skype

# Java
aptitude -y install sun-java6-jre sun-java5-jre

# Postfix
aptitude -y install postfix

#KDE Appz
aptitude -y install kopete konversation konqueror k3b amarok krfb ktorrent
aptitude -y install kftpgrabber kate kontact kdepim-kio-plugins kgpg
aptitude -y install akregator gdb

# Burn Programs
aptitude -y install gnomebaker

# GnuPGP Key Management
aptitude -y install seahorse file-roller

# aMSN
aptitude -y install amsn

# IRSSI / OpenSSH
aptitude -y install irssi openssh-server

# GnuMP3d
# aptitude -y install gnump3d

# OTR
aptitude -y install python-glade-1.2 python-gtk-1.2

# VmWare
aptitude -y install linux-headers-`uname -r` build-essential xinetd

# Browsers
aptitude -y install kazehakase opera flashplugin-nonfree

# Codecs
aptitude -y install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer

# VLC
aptitude -y install vlc

# Samba
aptitude -y install samba

# Midnight Commander
aptitude -y install mc

# UNRAR
aptitude -y install unrar

# GParted
aptitude -y install gparted

# CheckRootKit
aptitude -y install chkrootkit

# OpenOffice
aptitude -y install openoffice.org openoffice.org-gtk

# ImageMagic
aptitude -y install imagemagick

# Numlock & fonts
aptitude -y install numlockx msttcorefonts

# Timeserver
aptitude -y install ntp ntpdate

# HDD Encryption
aptitude -y install cryptsetup hashalot

# various
aptitude -y install whois phpmyadmin mysql-server mysql-client libmysqlclient15-dev adesklets d4x googleearth htop traceroute libjack0.100.0-dev

#######################
#######################

# Restore other files

cp -f backup_files/sysinfo /usr/share/apps/konversation/scripts/sysinfo
cp -f backup_files/screenshot /usr/bin/screenshot

```

---

### Post by stuckwithwindows on 2008-06-06
> **tomcheng76 said:**
> Try SBackup
[http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

Have you tried this? But seems a try.

---

