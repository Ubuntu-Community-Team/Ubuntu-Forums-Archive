---
title: "scheduled startup"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by m666 on 2006-02-14
Is there any command/application/tool allowing scheduled system startup/shutdown?
It is nice feature in Mac OS, I'd like to use it also in Linux

---

### Post by taurus on 2006-02-14
Not sure about the startup thing but you can use crontab to shutdown your machine at a specific time!!!

---

### Post by patrick295767 on 2006-02-14
[QUOTE=m666]Is there any command/application/tool allowing scheduled system startup/shutdown?
It is nice feature in Mac OS, I'd like to use it also in Linux[/QUOTE]

/etc/crontab

u may use at the beginning kcron.

Look mine: /etc/crontab
```
 #This file also has a username field, that none of the other crontabs do.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h dom mon dow user	command
17 * * * *	root	run-parts --report /etc/cron.hourly
# 
25 6 * * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
# 
47 6 * * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
# 
52 6 1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
# Please be informed tthat I am stopping gdm
0,30,55 0,23 * * *	root	/etc/init.d/gdm	stop
# Please be informed tthat I am stopping kdm
0,30,55 0,23 * * *	root	/etc/init.d/kdm	stop
# I start the gdm
0 7 * * *	root	reboot

# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.


```

Greetings,

pat

---

