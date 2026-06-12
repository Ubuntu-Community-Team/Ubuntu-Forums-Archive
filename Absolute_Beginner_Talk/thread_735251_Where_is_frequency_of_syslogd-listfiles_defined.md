---
title: "Where is frequency of syslogd-listfiles defined?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by jakeo25 on 2008-03-25
Using an older Debian release, and working with a custom driver, I noticed kern.log file not being rotated when I expected.  Plus, the first level rotation, kern.log.0 and syslog.0 are uncompressed (bug in savelog?)

the /etc/cron.weekly/sysklogd and /etc/cron.monthly/sysklogd tasks issue, syslogd-listfiles  and syslogd-listfiles -w, respectively to generate a list of files to savelog.  kern.log is not in the daily list NOR the weekly, as I expected.  I noticed kern.log shows up with the -a option.

I noticed my Ubuntu 7.10 does indeed have the kern.log in the daily list. 

Where do log files get added such that syslogd-listfiles 'knows' they are weekly or dailly (or monthly)?  syslog.conf only seems to define which files, but not the frequency.

Thanks in advance.

Jake

---

### Post by zen_waters on 2008-03-26
I am a little unclear on what you mean.

---

### Post by (((X))) on 2008-03-26
Hello, Jake

Logrotation, go to /etc/logrotate.d/
and open a file you need, there will be a line in that has rotate 7, change 7 to 4, for example to keep logfiles for 4 days.

---

