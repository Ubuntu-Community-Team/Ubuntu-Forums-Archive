---
title: "CRON is not working!!!"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by 09adi09 on 2007-01-18
Hi everyone.

I modified my /etc/crontab to look like this,

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom(1-31) moy(1-12) dow(0-6-Sun to Sat) user command
**30 * * * * root /bin/echo "Hello! Cron from /etc/crontab"**
17 * * * * root run-parts --report /etc/cron.hourly
25 6 * * * root test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6 * * 7 root test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6 1 * * root test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

This iis not working..I want to demonstrate to myself a working of cron..
What am i doing wrong?

---

### Post by frodon on 2007-01-18
Double post, please don't open more than one thread for a question.

[http://ubuntuforums.org/showthread.php?t=341053](http://ubuntuforums.org/showthread.php?t=341053)

Thread closed

---

