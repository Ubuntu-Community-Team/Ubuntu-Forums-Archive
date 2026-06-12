---
title: "Daily Cron Job"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by vanthai26 on 2006-11-13
Hi

I am running a Ubuntu server and trying to set up a daily cron job for a task. I wrote a script and drop it into /etc/cron.daily folder on ubuntu and waited but the script never get run.I always thought to set up a cron job in ubuntu all I have to do is to drop the script into the appropriate folder(dail, weekly..). Am I missing any step here?

Please help

Thanks

---

### Post by mo79 on 2006-11-13
> **vanthai26 said:**
> Hi

I am running a Ubuntu server and trying to set up a daily cron job for a task. I wrote a script and drop it into /etc/cron.daily folder on ubuntu and waited but the script never get run.I always thought to set up a cron job in ubuntu all I have to do is to drop the script into the appropriate folder(dail, weekly..). Am I missing any step here?

Please help

Thanks

The command: 

crontab -e

will open (or create if not existing) your crontab file. The format for a cronjob is e.g:

01 04 1 1 1 usr/bin/somedirectory/somecommand

(first number is minute, second is hour, third is day, fourth is month, fifth is weekday, followed by the command (full path as above preferred).
A '*' (without quotes) can be used to indicate command repeating (e.g. every minute, every hour etc.)

Different cronjobs go on different lines in the same file.

---

### Post by vanthai26 on 2006-11-13
This is the technique that I am currently using to running cron job but I always thought that if you drop the script into /etc/cron.daily then you don't have to set the "crontab -e"
I thought it is automatically run for you. I could be wrong..

---

### Post by mo79 on 2006-11-13
> **vanthai26 said:**
> This is the technique that I am currently using to running cron job but I always thought that if you drop the script into /etc/cron.daily then you don't have to set the "crontab -e"
I thought it is automatically run for you. I could be wrong..

Could be, but as a desktop user who just read a chapter from the holy Official Ubuntu Book, it's the word sent forth. ;) I'm guessing the crontab -e command is the equivalent of saying "Oi, Ubuntu! Bring up my crontab, you know where it is, make it up if it's not there, wherever it should be."

I need refreshments..

---

