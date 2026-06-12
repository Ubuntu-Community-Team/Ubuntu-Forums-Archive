---
title: "Kcron: how to do /etc/gdm stop  (please could u check my crontab below) ?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-12-18
Hi, 

I installed kcron in order to plan a gdm stop in the evening for my familly.

I run kcron as root; ok , 
And in the kcron window there is a lot of possibillities ; names of users ... gdm bin ... and so on
I put in the systemcrontab and also in the gdm the following :

/etc/init.d/stop 
for 11pm
and so on;...
-(every day)  
  
Results: Not working ... 
Why ?? what's wrong in it ?
Please find below the content of /etc/crontab

Should I have restarted my linux box ?

Thank you very much
  
Patrick



```
# This file also has a username field, that none of the other crontabs do.
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
0,30,55 0,23 * * *	/etc/init.d/gdm	stop
# I start the gdm
0 2,3,4 * * *	/etc/init.d/gdm	start
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.

```

---

### Post by Seveas on 2005-12-18
[QUOTE=patrick295767]
0,30,55 0,23 * * *	/etc/init.d/gdm	stop
# I start the gdm
0 2,3,4 * * *	/etc/init.d/gdm	start
[/QUOTE]

The username is missing. It should be

0,30,55 0,23 * * *	root	/etc/init.d/gdm	stop
# I start the gdm
0 2,3,4 * * *	root	/etc/init.d/gdm	start

---

