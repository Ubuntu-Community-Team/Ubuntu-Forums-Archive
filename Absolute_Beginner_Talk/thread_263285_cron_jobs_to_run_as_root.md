---
title: "cron jobs to run as root"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by dkline on 2006-09-22
Ok I new to Linux, I'm a windows guy, but really loving Ubuntu so far.  How do I run a process as root from system boot up?  For example: how would I make darkstat run from system boot?  Right now I have to open a term, sudo -i then darstat.  How do I automate this to get darkstat running upon system boot?

---

### Post by chrisfay on 2006-09-22
```
sudo update-rc.d darkstat defaults
```

---

### Post by dkline on 2006-09-22
Great.  Now I guess I got ahead of myself.  I know what a cron job is but how do I set one up? Or is there something better to automate running a process in Linux other than a cron job?

---

### Post by chrisfay on 2006-09-22
Cron is the easiest way to schedule tasks. You can create simple scripts and drop them in the folders:

/etc/cron.monthly
/etc/cron.daily
/etc/cron.hourly

...and that script will be ran respectively. 

You can get much more detailed as far as the scheduling is concerened by creating crontabs that define specific timelines for your jobs/scripts.

There's a lot of documentation on creating crontabs, though if you don't need exact timing I would recommend putting your jobs in one of the cron folders for simplicity.

---

### Post by lkrubner on 2008-07-11
I've a follow up question. 

What folder exists for scripts to be called every few minutes? If I drop a script in /etc/cron.hourly I assume it only gets called once an hour. What about the folder /etc/cron.d? How often do scripts in that folder get called?

---

