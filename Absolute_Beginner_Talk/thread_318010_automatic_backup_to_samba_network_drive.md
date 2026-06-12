---
title: "automatic backup to samba network drive"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by rshel on 2006-12-13
Hi,

I've been using ubuntu for almost a year, but I'm not a tech person at all.  My question regards backups.  I have a home network with a Simpleshare network hard drive connected to a wireless router.  It appears as a Samba drive on to my Ubuntu PC.  I have no problem accessing the drive, but I have yet to figure out how to make automatic backups to it from my ubuntu pc.  I have tried rsync, simple backup, etc.  I mounted the simpleshare network hard drive through fstab and /mnt and have access to it but whenever i try to backup i get error messages that rsync, etc., don't have permissions to create directories, files, etc.  I have been using the gsync gui for rsync, if that is relevant. 

Here is my fstab line regarding the mount, if that helps:

//simpleshare/MyFolder /mnt/backup smbfs umask 000	0	0

Can someone point me to a simple step-by-step guide to automating backups like this.   I'm not afraid of the command line as long as the instructions are clear.

 I've read that simplifying the backup process is in the works for future ubuntu releases; I heartily endorse the effort. 

Thanks in advance!

rshel

---

### Post by stounfree on 2006-12-29
Hi rshel,

I'll show you how to make a shell script combining **smbclient** with the compression tool of your choice (i use bzip2 as an example).

smbclient is a command line tool for accessing SMB/CICS shares or services. you can install it as usual with apt-get (or aptitude) :

[SIZE="4"]Install smbclient[/SIZE]

```
sudo apt-get install smbclient
```

_I strongly advise you to read the man pages of smbclient_, especially the command section :

```
man smbclient
```

To be short, smbclient works just like ftp and has two modes :
[LIST]
[*]Interactive mode : runs your command then waits for another
[*]Batch mode : used in scripts
[/LIST]

[SIZE="4"]Write your backup script
[/SIZE]
Here's a little script that uses the batch mode. -N for no password, -c is followed by the command list (you can use cd, ls, mput, mget, etc., again see man smbclient). I suppose you'll save your script under /home/you/backup.sh, i use sudo so it will be protected by root ownership :
```

sudo vi /home/you/backup.sh

```

```

#!/bin/bash

#go to your backup dir
cd /path/to/your/backup

#create a Timestamp like this : 20061229130008
export TSTAMP=$(date +%Y%m%d%H%M%S)

#add timestamp to your backup filename
mv yourfile yourfile-$TSTAMP

#crompress with bzip2
bzip2 --best yourfile-$TSTAMP

#send you timestamped, compressed backup to samba share without a password
smbclient -N //simpleshare/MyFolder -c "prompt;ls;mput yourfile-$TSTAMP.bz2;quit;"


```

You should of course replace my paths and filenames with yours, But keep the timestamp if don't want to overwrite your previous backups each time.
 
Don't forget to make the script executable :

```
chmod u+x /home/you/backup.sh
```

For troubleshooting, you can add -v before -N to have more output.

```

smbclient -v -N //simpleshare/MyFolder ....

```


Test that your script works correctly :

```

sudo /home/you/backup.sh

```

[SIZE="4"]Schedule your backup using cron :
[/SIZE]
if you want to use predefined cron periodicity then copy your script to one of these folders :
```
sudo cp /home/you/backup.sh /etc/cron.daily
```
Or
```
sudo cp /home/you/backup.sh /etc/cron.hourly
```
Or
```
sudo cp /home/you/backup.sh /etc/cron.monthly
```
Or
```
sudo cp /home/you/backup.sh /etc/cron.weekly
```

Otherwise you you should edit /etc/crontab :
```

sudo vi /etc/crontab

```

**add** this entry to it and customize it, In this example, It runs the backup as root each 12th day of the month  at 16:30 :
```

30 16 12 * *   root    /home/you/backup.sh

```

I think you should restart cron after all this :
```

sudo /etc/init.d/cron restart

```

I think that's all you need. I hope it works for you and it helps. Let us know if you have more questions.

Regards,

Stounfree

---

### Post by rshel on 2007-05-03
Thanks for the help.  This looks like a very useful script.  One question.  Do I need to mount the samba network drive in my fstab before I can name a path to it?  Sorry if this is a dumb question; I had this working a while back but have been actually productive in my job and not had time to mess around with the inner workings of my computer and so have forgotten what I need to do to be able to name a path to a network drive from the terminal.

---

### Post by stounfree on 2007-05-04
You don't need to mount the samba share in your fstab since the script will dynamically connect to the share each time you'll run it. 

The following command (included in the script) will connect to this samba share : \\simpleshare\MyFolder, puts your bzipped backup (file yourfile-$TSTAMP.bz2)  in it and disconnects without requiring a mount or a user action :

```
smbclient -N //simpleshare/MyFolder -c "prompt;ls;mput yourfile-$TSTAMP.bz2;quit;"
```

---

### Post by rshel on 2007-08-31
This has worked great for many files, but why is it that when I try to use it with the Simple Backup gnome utility that it won't move the files?  Actually, it seems to copy the files but in fact it just creates a file with the *.ful name, which is an empty text file.

---

