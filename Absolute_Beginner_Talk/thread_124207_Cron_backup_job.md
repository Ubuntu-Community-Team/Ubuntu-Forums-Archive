---
title: "Cron backup job"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by akniss on 2006-01-31
Hi all.  I'm setting up an Ubuntu box at work for some simple data entry.  I have installed a second hard drive to use as data backup storage.  What I want to do is this:  every night (around 2 am when the computer is not in use) tar all files in the data directory and store them on the backup hard drive.  I think it would be simple to use a cron job to do this, but I'm not sure how.  Below is the command that *i think* will perform the backup that I want.
```
 tar zcvf /media/backup/Backups/$(date +%a_%m_%d_%Y).bkp.tgz /home/weeds/Desktop/Data/

```
How do I schedule this to run every night?

---

### Post by frodon on 2006-02-01
Good links about cron jobs : 
[http://www.ubuntuforums.org/showthread.php?t=93611](http://www.ubuntuforums.org/showthread.php?t=93611)
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

---

