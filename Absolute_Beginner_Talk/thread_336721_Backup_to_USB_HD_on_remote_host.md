---
title: "Backup to USB HD on remote host"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by misterpms on 2007-01-12
I'm having trouble creating a script to back up my files to a removable USB harddrive attached to a remote machine. I've already made a shell script to backup my files to the remote machine (not the USB HD), I put it into a crontab and it works fine. The code for daily_backup.sh is below:
```

#!/usr/bin/sh
#Author: misterpms
#Date: 08-01-2007
#NOTE: The exclusion of hidden files is very crude. It might
#be more prudent to make a file with exclusion regexps

#Backup Host
HOST='xxx.xxx.xxx.xx'

#Source Folders
SRC="$HOME/ToBackUp/"

#Destination Folders
DEST="$HOME/Backup/"

#Rsync options
#-a, archive mode; -v, increase verbosity; 
#-z, compress file data during the transfer
OPTIONS='-avz'

rsync $OPTIONS -e 'ssh' --exclude='.*' $SRC $HOST:$DEST

```

However problems arose when I tried to modify the file to store my files on the USB HD; Ideally I'd like a script that can be put into a weekly cron. The relevant (remote machine) /etc/fstab of the USB HD is
>  /dev/sda2       /media/usb      ext3     defaults,user,noauto  0  0

I've tried sshfs, but I couldn't mount the USB HD on my local machine (mentioned in the how-to that I was following). I then googled for over an hour, but gave up and decided to try the following:
> 
ssh misterpms@$HOST "mount /dev/sda2" 
sh daily_backup.sh
ssh misterpms@$HOST "umount /dev/sda2"

it's very crude, but it works (with the appropriate modification of the DEST variable). Is there a better way to do what I need ?

Thanks in advance!

NB: I can't change the /etc/fstab on the remote machine (an auto option would make life much simpler!) and a few people will be using the USB HD backup script so using sshfs to mount locally may be out of the question.

---

### Post by misterpms on 2007-01-12
If anyone is interested I have reposted the [COLOR="Red"][here]("http://ubuntuforums.org/showthread.php?p=2002094#post2002094")[/COLOR]

---

