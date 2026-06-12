---
title: "rsync-ing my drives to a backup external drive"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by psychofish on 2007-10-27
I'm dual booting into Gusty and WinXP, and I have all my photos, music, movies, etc on a 300GB ntfs-formatted drive. On WinXP I've got a backup program that backups all that data every night on an external hard drive called CLYMENE. I'm using rsync on my Gutsy install so that when I'm in Ubuntu for several days the backups don't stop. Currently I have my crontab set up with this line:

```

10 3 * * * rsync -a -vv --progress --stats --delete --modify-window=1 --exclude "/RECYCLER" /media/sdb1/ /media/CLYMENE/dee/ > /media/CLYMENE/dee.rsync.log
```

couple of questions.
1) I have it to output to a log right now, but is there a way to have information also show up in a terminal as it does its job?
2) is there a better way of showing maybe only errors?
3) what if my external drive isn't mounted at the time (say if I turn it off or take it somewhere else temporarily) does the script fail gracefully? it wouldn't kill any of my data would it?

thanks!!

---

### Post by PetePete on 2007-10-27
ive got a similar setup, wrote a script which checks if the drive is connected, if it is then it rsyncs. 
dont think you could make it pop-up a terminal when it does it, not unless you set cron to open a program/script which launches the terminal...... also not sure about only outputting errors.

anyway heres my script, you'll need to change drive locations etc

```

#! /bin/bash
date=`date +'%d-%m-%Y'`
start_time=`date +'%s'`
echo "started"

if [ -d /media/disk ] ;  then {

        echo "backing up started on: $date" >> /home/pete/scripts/homeBackupOutput

        rsync -a --delete /home/ /media/disk/home

        end_time=`date +'%s'`

        et=`expr $end_time - $start_time` >> /home/pete/scripts/homeBackupOutput


        echo "Finished in: $et " >> /home/pete/scripts/homeBackupOutput
        echo "" >> /home/pete/scripts/homeBackupOutput
}

fi

```

---

### Post by psychofish on 2007-10-28
I gave the shell script a try and I couldn't seem to get it to work at all-- I could run it manually, but in cron it doesn't seem to do anything. I did a little more checking around and a friend told me about rsnapshot which would supposedly do that checking for me. It's already in the Ubuntu packages as "rsnapshot".

I'm going to give that a try... just thought I'd mention it in case someone else is looking for something similar.

---

### Post by Beaucephus on 2007-11-08
I have a few automated scripts that I like to watch happen.  I use the command
```
gnome-terminal -x nameofscript
```
That opens a terminal and runs the script in it.  If you want to get real fancy check out **zenity**.

Here is a good link on an overview of zenity
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/]("http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/")

---

