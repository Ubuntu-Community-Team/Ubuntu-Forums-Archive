---
title: "[SOLVED] Where am I messing up with cron?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by TreverT on 2007-11-10
I'm trying to setup some basic backup scripts to run using cron, to rsync various directories to remote locations.  I have written backup.sh, backupdaily.sh, and backupweekly.sh scripts, marked them all executable, and dropped them into the appropriate cron.hourly, cron.daily, etc directories.  

My understanding was that this was all that was needed - drop the scripts in the right directories and cron would run them on its own.

But, nothing is being run.  I have manually run each of the scripts and all work properly, so I know the scripts themselves are functional - they're just not being run for some reason.  What do I do next?  This is all totally new to me.  I've looked around on the web but nearly all the cron instructions I find are focused on editing crontab with very specific times, and I don't need that specific usage.

Being curious if  cron was running, I entered:
 ps aux | grep crond
trevert  28681  0.0  0.0   2976   752 pts/0    R+   22:48   0:00 grep crond

I don't know what this means but maybe it will help someone help me out.

Edit:  Oh, in case it provides any clues, here is the content of my crontab file in /etc:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

---

### Post by matthewcraig on 2007-11-10
What is the script you are trying to run?  How are you determining it is not being run?

---

### Post by TreverT on 2007-11-11
> **matthewcraig said:**
> What is the script you are trying to run?  How are you determining it is not being run?

Here's one of them - just a very simple backup script:


rsync -avzru /media/HP_PAVILION/OurExcelMoney /media/Maxtor/Backups
rsync -avzru "/media/HP_PAVILION/Documents and Settings/Propriétaire/Mes documents/Book Collector" /media/Maxtor/Backups

I know it isn't being run because the files in the backup directory aren't changing to reflect changes in the main files.  If I run this script manually in a terminal, it works properly and updates the files on Maxtor.  Yet it sits in the cron.hourly directory and never gets run by cron.  Is ssomething else required to make cron run it, other than just dropping it in cron.hourly?

---

