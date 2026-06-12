---
title: "crontab setup"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-11-12
I am trying to make a crontab file to run several script files. My crontab file looks like this:
> 15 00 * * 6 /etc/cron.weekly/thumbnail_cleaner

When I run the crontab file to test it I get this error:
> "/etc/cron.weekly/thumbnail_cleaner":1: bad minute
errors in crontab file, can't install.

---

### Post by alienexplorers on 2007-11-12
I know there are plenty of smart people on this forum.  Can one of you give me the time needed to resolve my problem.

---

### Post by drs305 on 2007-11-12
Does your crontab file have a blank line on the end? I believe it should.

---

### Post by alienexplorers on 2007-11-12
I do have a blank line at the end of my crontab file.

---

### Post by drs305 on 2007-11-12
In the help sections I've read, the hour entries are 0-23 so the second entry should probably be 0 instead of 00. Sorry I missed that the first time.

---

