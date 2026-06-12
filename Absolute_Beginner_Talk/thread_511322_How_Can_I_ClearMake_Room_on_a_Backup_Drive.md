---
title: "How Can I Clear/Make Room on a Backup Drive?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by lakelovers on 2007-07-27
I have a small, second HD (6.01 Gib) that I use for backups with "Simple Backup." It didn't take long to fill the drive and now I don't get backups. Is there a way I can free space without formating the drive? And is there a way or program I can use that will automatically delete really old files to make room for new files? The drive has only one partition. Does Simple Backup compress files? I don't see an option for that action.

---

### Post by FleetAdmiral74 on 2007-07-27
You can delete some of the files to free up space without formating. I believe you click on the file and press delete.

PartImage can compress files, another backup software. Does the whole partition though, so will not work if you are backing up a lot.

---

### Post by DBStevens on 2007-07-27
Take a look at the directory your backups are in I believe (if I'm looking at the correct script) that you'll find files named in the following form something.tar.bz2 which was produced by the tar command using the options -cjf and thus the backups are compressed.

There is also a script that comes with SimpleBackup (If I'm looking at the package you have installed) called expirebackups it lists all prior backups that are older than 4 generations.  Those would be candidates for deletion assuming that 4 levels of backups is enough for you.

---

### Post by lakelovers on 2007-07-27
My backup files are in /second_drive/lost+found, and I don't have permission to examine the files. I've tried as root, but still cannot see the files unless I not using the correct terminal command. I've tried "ls" but get no response. I guess I need to change the permisisons though on the property screen it says that root has permission to view and write to the folder.

I have the lastest version provided on Synaptic, but on the Simple Backup site, there is a more current version, which I should probably install. I just installed the Simplebackup tool utiltiy (version .0.0.8-1ubuntu) but haven't examined it.
> 

There is also a script that comes with SimpleBackup (If I'm looking at the package you have installed) called expirebackups it lists all prior backups that are older than 4 generations. Those would be candidates for deletion assuming that 4 levels of backups is enough for you.


I don't see an option for "expiredbackups" on my version.


EDIT
Now, I'm confused. I have "sbackup" which I have been using for sometime. It appears on my System/Administration list. As I said, above, I just installed "Simplebackup" which is on the Synpatic program list. The "Simplebackup" app appears to be more flexible from what I read on the Simplebackup site. However, I cannot open the app. When I do a search I find it with a lot of files, but I cannot find it in the appplications list.. I tried opening it in the terminal but I'm not giving the correct command to open it. So, how do I open this second Simplebackup?

---

### Post by DBStevens on 2007-07-27
It isn't an option it is another script that is part of the SimpleBackup package.  You'll see it in the installed files list if you go to Synaptic and ask for information on the installed package.

In terminal do:

man expirebackups

that should tell you what that script does.

It is installed along with the script that does the backup.

Could you post your configuration information for SimpleBackup.

In terminal can you 

sudo cd /second_drive/lost+found 

then type

sudo ls -o

---

### Post by st33med on 2007-07-27
Usually, whenever I resized my Windows partition, the data remains the same.

---

### Post by DBStevens on 2007-07-27
You are talking about the sbackup package which is known as Simple Backup Suite and is the package sbackup  there are several backup packages including one called Simple Backup which is package 
SimpleBackup.

Oh well such is life.
.

---

### Post by lakelovers on 2007-07-28
Life is complicated. This is what is the config file: (I have not configured simplebackup because I can't run it)

# $Id: simplebackup.conf,v 1.8 2005/12/02 19:37:36 mitch Exp $
# Configuration file for simplebackup.

#
# This is the directory where the backup is written to.
# Be sure to have enough free disk space here.
#
TARGETDIR=/backup

#
# This is the directory where the backup is prepared.
# Disk space needed here is the sum of all data to be backed up.
# This directory will be deleted on startup, so don't point to
# anyting important.
#
WORKDIR=$TARGETDIR/tmp

#
# These paths and their subdirectories are to be backed up.
# Use : to separate multiple paths.
#
BACKUPDIRS='/boot:/etc:/root:/var/backups:/var/games:/var/lib/amavis-stats:/var/lib/aptitude:/var/lib/cvs:/var/lib/mailman:/var/lib/news:/var/lib/ucf:/var/lib/usemod-wiki:/var/log:/var/mail:/var/spool/cron'

#
# This is the name of the backup.  It is later prepended
# with a timestamp.
#
NAME=$(hostname)

#
# This lockfile is used to detect another running backup.
# You can run multiple different backups in parallel by
# using different lockfiles in different configurations.
#
LOCKFILE=/var/run/backup_in_progress-"$NAME"

#
# Nice level to run with.
# 20 is low priority, 0 is normal,
# -20 is high priority (only root can do this).
#
NICELEVEL=20

#
# Chroot path.Ubuntu 7.04 Feisty Fawn User
# If you want to backup another system that is reachable via
# your filesystem, you have to point this variable to the other
# system's root directory.  Leave empty for normal operation.
#
CHROOT=

#
# These commands are executed before the backup.
# Here you can dump databases, save your partition layout etc.
# extracommand() is executed before entering a possible CHROOT.
#
extracommands()
{
    # system data
    echo "extracting system data"
    fdisk -l > "$WORKDIR"/output_fdisk_-l
    lspci -v > "$WORKDIR"/output_lspci_-v
    dpkg --get-selections > "$WORKDIR"/output_dpkg_--get-selections

    # dd if=/dev/hdb  of="$WORKDIR"/mbr_hdb.dd bs=512 count=1
    # dd if=/dev/hdc1 of="$WORKDIR"/bootsector_hdc1.dd bs=512 count=1

    # when using CHROOT, commands need to be changed, e.g.:
    # chroot "$CHROOT" dpkg --get-selections > "$WORKDIR"/output_dpkg_--get-selections
    # instead of just  dpkg --get-selections > "$WORKDIR"/output_dpkg_--get-selections

    # databases
    #echo "dumping databases"
    #(
    #    cd "$WORKDIR"
    #    /root/aniki-tools/dumpit.sh
    #    /root/forum-tools/dumpit.sh
    #    /root/mysql-tools/dumpit.sh
    #)
}

#
# These commands are executed after the backup.
# The new backup filename is available as $BACKUPFILE.
#
postbackup()
{
    # echo mailing disk space left 
    # df -h "$TARGETDIR" | mail -s "backup finished" root

    # echo mailing new archive 
    # mutt -a "$BACKUPFILE" -s "backup finished" root < /dev/null

    # echo scopying new archive
    # scp "$BACKUPFILE" backupuser@somehost:/some/dir
}


I've tried opening simplebackup in the terminal but I get a message that it doesn't exist.

Here's what Synaptic says is installed


/.
/usr
/usr/bin
/usr/bin/simplebackup
/usr/bin/expirebackups
/usr/share
/usr/share/doc
/usr/share/doc/simplebackup
/usr/share/doc/simplebackup/README
/usr/share/doc/simplebackup/HISTORY
/usr/share/doc/simplebackup/copyright
/usr/share/doc/simplebackup/examples
/usr/share/doc/simplebackup/examples/simplebackup.conf
/usr/share/doc/simplebackup/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/simplebackup.1.gz
/usr/share/man/man1/expirebackups.1.gz
/usr/share/man/man5
/usr/share/man/man5/simplebackup.conf.5.gz


However, when I do a search of system files I get this:

[IMG]http://home/jerry/Desktop/Screenshot.png[/IMG]

Well, obviously, I don't know how to load an image.

I apologize for all the copying. where do I go from here. I just want to run simplebackup.

---

### Post by DBStevens on 2007-07-28
If you try running simplebackup without configuring it like this:

$ simplebackup

You get a nastygram like this:

stat: cannot stat `/home/userid/.simplebackup.conf': No such file or directory
/usr/bin/simplebackup: line 42: /home/userid/.simplebackup.conf: No such file or directory

If you place a copy of the the configuration file in your home directory you get further.   How well it goes depends on your permision settings and how you run the script. 

However this doesn't exactly help with your original questions which really revolve around sbackup.

I did install sbackup but I haven't gotten around to play with it.  But like any backup system if you delete the backups you'll free up the space and should be able to continue doing backups, the question however becomes which files can I get rid of.

Simple Backup actually has a script that displays what it considers to be excess backups.

Maybe I'll try sbackup in a bit just to get a feel for how it works..

---

### Post by DBStevens on 2007-07-28
Progress report on sbackup:

1: Still running
2: Produces a tgz file which is compressed.
3: Is probably having fun wading through my rather large file system.

---

### Post by lakelovers on 2007-07-28
Thanks for the progress report. I keep messing around getting nowhere.
Jerry

---

### Post by DBStevens on 2007-07-28
Do not run any commands until you have read and _understand_ all of the following.

Ok if you are using sbackup and you can get to the backup directory  which you told me was /second_drive/lost+found

You'll have to have superuser access through your file manager  I did a sudo bash in terminal so I could do the cd to my backup didrectory and run my commands.

If you do a ls -Ro you should see a pile of directories that end in .ful and .inc the .ful ones are full backups and the .inc ones are since the last .inc or .ful for a given day (I think, you'll be able to tell I can't yet, a day hasn't past) what I did afer running several manual backups was to do a rm -rf *.inc which removed the .inc directories and then ran a manual backup it then built a larger .inc backup than any of the previous .inc backups.

Since I didn't have multiple days worth of backups I couldn't cause any problems by doing the forced removal of all .inc backups if you have more than one days worth of backups you should not use the find and destroy mode of doing the rm command you should be more selective.  I see the purge function may be of some use I don't know if you have set that up.

---

### Post by lakelovers on 2007-07-28
OK, I'm with you. I see all the files (.ful, .inc, and others). I haven't deleted any yet. How would I use the rm command to delete dated files, say three or four months past rather than all .ful or .inc files? I'm puzzled by one thing. On the sbackup restore list, it goes back to Feb - April. None  of the May - July, show. However, on the terminal list goes back to June 20 (the last full backup). It would seem that the restore list should reflect the terminal list (or vise versa).

---

### Post by DBStevens on 2007-07-28
Well if it were me I'd probably delete the directories by the date in the directory names.  If you can do it in the file manager it shouldn't be too hard.     Using terminal and being insde the backup directory you could issue rm -fr 2007-02* to get rid of February backups rm -fr 2007-03* for March just be careful with the names since the rm is being used in both force and recursive mode along with a wildcard  of * you can easily delete the entire contents of the directory.  Remember command mode is powerful and with that power comes danger.

---

### Post by lakelovers on 2007-07-28
Thanks for all your help. I think I have control of the backup files for sbackup. Following your direction, I deleted backup files for Feb - March. That opened up about 5 Gib on my 6.01 Gib HD. I didn't expect it to open that much but that's good. Then I did a manual full backup and that took 2 Gib, leaving a bit over 4 Gib. It's quite evident that I need a bigger HD for backups but I don't want to spend the bucks. I'd still like to take a look at SimpleBackup which has the "expired" file option but running that app is still a puzzle. Can't do it. I re-installed the app. I still get the message that there's no simplebackup file or config file even though all show up when I do a search. There must be a simple answer.

---

### Post by DBStevens on 2007-07-28
As for Simple Backup that file you pasted in this thread at message #8 is the coniguration file and should be copied to your home directory as .simplebackup.conf ,  to configure this system you use a text editor and make changes to that file.  Ah, the old fashioned way.

---

