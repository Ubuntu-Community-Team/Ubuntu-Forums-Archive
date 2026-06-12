---
title: "Noob question: how do system log files work?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by oldsmobile_mike on 2008-03-04
Okay, here's a noob question for you:  ;-)

Can anyone explain how the system log files work, or give me some pointers where to read up on them?

I'm just exploring the contents of /var/log for the first time, and have noticed, for example, files like:

debug
debug.0
debug.1.gz
debug.2.gz
debug.3.gz

Am I correct in assuming that "debug" is the most current, debug.0 is the next-oldest, and so on, and that it appears as if older ones get archived, and then deleted after a certain period of time?  Is this what it's doing?

(I see the same thing for dmesg, messages, etc.)

Thx!

---

### Post by hyper_ch on 2008-03-04
yes, to not overgrow the logs it will "archive" older logs into compressed files (gz) and after a while delete them altogether.

---

### Post by Joeb454 on 2008-03-04
You seem to have picked it up pretty quickly, that's exactly what it is, though I couldn't tell you how often it archives them, I'm sure somebody knows though :)

---

### Post by kpkeerthi on 2008-03-04
To understand how logs are archived type in a terminal ```
man logrotate
```

---

### Post by kpkeerthi on 2008-03-04
[http://www.ibm.com/developerworks/linux/library/l-roadmap5/](http://www.ibm.com/developerworks/linux/library/l-roadmap5/)

---

### Post by ruy_lopez on 2008-03-04
see inside /etc/cron.daily /etc/cron.weekly /etc/cron.monthly. These include the scripts which rotate the log files. Some are handled by logrotate, in which case they'll be inside /etc/logrotate.d/.

Most of the system log files are rotated using /etc/cron.*/sysklogd. The script uses `syslogd-listfiles` to enumerate the logfiles. 

See 'man syslogd-listfiles' and it'll show you how to display a list of log files, and when they are rotated.

---

