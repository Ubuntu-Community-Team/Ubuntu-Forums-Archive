---
title: "crontab on rhythmbox"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by davidY on 2007-01-01
Hi, I would like to use crontab to control my rhythmbox to start playing music at a certain time. This would be done like this: 

crontab -e
insert: 40 7 * * * rhythmbox --play

however, at 7:40 it does not work. I was testing it by setting the crontab time to just two minutes after the current time. However it never works. Any ideas why?

---

### Post by davidY on 2007-01-01
Well, here is what I want to do: kill rhythmbox, load it with another database, and play that at a certain time. Now this code works, but does not do anything when it is being done by cron. Why?

```
#kill current rhythmbox
if ps ax | grep -v grep | grep "rhythmbox" > /dev/null
then
	/usr/bin/rhythmbox -quit
	sleep 2
fi

#load second profile - sleep profile
/usr/bin/rhythmbox --rhythmdb-file=/home/david/.gnome2/rhythmbox/rhythmdb2.xml --toggle-hide &

sleep 2

#play from that profile
/usr/bin/rhythmbox --play &

```

---

### Post by twowheeler on 2007-01-01
Well, the format of the crontab line is supposed to be:

 minute hour dayofmonth month dayofweek user  command

which is seven fields, but you have six in your crontab line:

40 7 * * * rhythmbox --play

So maybe it is interpreting 'rhythmbox' as the user, and '--play' as the command, and failing.

Just a guess.

You could also check the obvious things, like that your script is executable, that it starts with a #!/bin/sh, etc.

---

### Post by davidY on 2007-01-01
Oh, dont worry about errors in the time, i added an echo "a" > /home..... and the file is correctly written. so the script is writing, but it is not efffective for some reason.

btw, i just tried to make cron run any other gui app at a certain time, and it has all failed... why is that?

---

### Post by twowheeler on 2007-01-04
Hmm, well, just guessing again, but here is a thought.

What user is the script using when running rhythmbox?  From cron, normally it would be root.  Is there a X windows server available to the root user?  I am wondering if there is no GUI available to the root account, and that would cause rhythmbox to fail.  Try this: login as a normal user, and in a terminal window run the script as root (with a sudo command) and see what happens.

Have you checked the logs for errors from cron?

Cron can be weird, anyway.  I once tore my hair out trying to get a backup script to run from cron, and it just would not go.  It was /etc/cron.daily/backup.sh.  Then by chance I changed the name to backup, with no .sh, and now it works.  Go figure.

---

### Post by davidY on 2007-01-06
Ah I piped out the standard error and found out that rhythmbox requires gtk+ to run, except the screen variables are nto set in cron jobs. SOlutions - run some sort of commandline for it. This turns out to be far too unpractical.

I suggest using mplayer a commandline equivalent of gmplayer, which boasts handling any type of file, file lists, shuffling.

---

