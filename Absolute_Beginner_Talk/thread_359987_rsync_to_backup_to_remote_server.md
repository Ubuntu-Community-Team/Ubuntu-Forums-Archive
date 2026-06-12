---
title: "rsync to backup to remote server"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by mfdc1969 on 2007-02-12
Greetings,

I am new to Linux/Ubuntu and experimenting with rsync to backup my machine to a remote server. My ultimate goal is to make a nice simple script that can be automated to backup nightly without my being present and generate a log on my desktop.

I had success backing up /home after creating a RSA Key w/o passphrase which I then copied to the remote machine. Now I would like to add /etc directory and schedule a script. After reading MAN pages for rsync and scouring the forums I have arrived at a potential rsync command - I would love to have opinions/feedback on this:

rsync -e ssh -azvqpt -P -n --temp-dir=/tmp/bu_tmp/ --stats --include=/etc/ /home/michael michael@192.168.2.33:/home/backups/ubuntu-desktop >> /home/michael/Desktop/rsync_log

Are there any realistic dangers of using the rsync option --delete ?

So, if I add the above command to a file and name it /home/michael/backup.sh how do I get it automated to run in the early hours of the morning - say 1 AM?

I have added my user name 'michael' to the file /etc/cron.allow now do I simply create a terminal command as described in the man page for crontab?
crontab [ -u michael] /home/michael/backup.sh

---

### Post by nickburns on 2007-02-12
The best way to get the job to run at a specified time is to set up a cron job.  

You can set it up to run certain days, hours, minutes, months...

If you 'man crontab' it should give you what you want.

---

### Post by nickburns on 2007-02-12
Sorry misread your post

crontab -e

will get you to your crontab editor, there is where you specify times and the path to your .sh file

---

### Post by mfdc1969 on 2007-02-13
Thanks for the reply ... so crontab -e and then as below it should run at 1AM every night?
[INDENT][/INDENT]0 1 * * * /home/michael/backup.sh

Any comments on my rsync command syntax? I just read the MAN and built up what seemed to be the most options I needed ...

Seems too easy ... why have I spent so much time looking for a GUI app to do this ...](*,)

---

