---
title: "Kcron question"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-30
When a cron is done though Kcron, is it ran in sudo mode? If not, how can I run a sudo admin command?

---

### Post by amitroy5 on 2007-09-01
bump

---

### Post by amitroy5 on 2007-10-04
bump

---

### Post by indytim on 2007-10-04
I believe (based on my very limited experience building bash jobs to be run in CRON), that CRON is run at the root level.

IndyTim

---

### Post by hyper_ch on 2007-10-04
You know how to write crons manually?

---

### Post by indytim on 2007-10-04
I usually write the bash file and get it working.  After I'm satisfied that it is good-to-go, I move a copy to /usr/local/bin.  After that I make it executable.  Finally using KCron (I'm on Kubuntu) I schedule the CRON job.

Here's a small example of a backup I'm running for my local web server:

[PHP]
#!/bin/bash  
#	This program will run the backup of the Apache Web Server Programs to the backup partition
#

#of=/media/LxBackup/Server-BU/www/www-$(date +%Y-%m-%d).tar.gz
#tar -cvzf $of /var/www

rm -rd /media/LxBackup/Server-BU/www/*
cp -rp /var/www /media/LxBackup/Server-BU/www
[/PHP]

Hope helps.

IndyTim

---

