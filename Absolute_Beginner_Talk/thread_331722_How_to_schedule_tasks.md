---
title: "How to schedule tasks?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by yuliang on 2007-01-05
Should I use crontab?

---

### Post by 23meg on 2007-01-05
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by yuliang on 2007-01-05
As a test, I created a crontab file. Below is what I get

[I]yuliang@thinkpad:/$ crontab -l
47 0 * * * /usr/bin/firefox[/I]

But it doesn't work. Why?

---

### Post by yuliang on 2007-01-05
Do I need to run the command *cron* at the first place? But here is what I got

[I]yuliang@thinkpad:/$ cron
cron: can't open or create /var/run/crond.pid: Permission denied
yuliang@thinkpad:/$ sudo cron
cron: can't lock /var/run/crond.pid, otherpid may be 4709: Resource temporarily unavailable[/I]

I am confused now.

---

