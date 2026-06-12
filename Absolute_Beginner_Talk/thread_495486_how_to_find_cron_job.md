---
title: "how to find cron job?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by adza on 2007-07-08
I am looking to find the cron job that creates this line in my server's syslog file...
> Jul  8 12:09:01 adza /USR/SBIN/CRON[3728]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
When i vi /etc/crontab this line is not there, however when i vi /usr/bin/crontab it appears as a compiled file (all 'random' chars etc).. how should i decompile this file to check for this line (and comment it out as i believe that this is crashing my server...)

---

### Post by jschudar on 2007-07-08
i dont know what user is doing it, so check with your regular user name and your root account

you type in a terminal: crontab -l

will list your crontabs.. crontab -e to edit

---

### Post by adza on 2007-07-08
from crontab -l there is none for root and none for only other user (adza)?? but something is creating this line... ?? I've been stumped on this one for a while now.....

---

### Post by jschudar on 2007-07-08
[http://www.techiegroups.com/t126123-root-cmd-usrlibphp5maxlifetime.html]("http://www.techiegroups.com/t126123-root-cmd-usrlibphp5maxlifetime.html")

---

### Post by adza on 2007-07-08
thanks for that post, it does just seem to be housekeeping.. somehow i need to diagnose why that's the last line in my syslog every time before intermittent system crash.... :S

---

