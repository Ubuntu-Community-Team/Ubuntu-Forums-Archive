---
title: "Cron"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by ZiLOG_Z80 on 2006-05-10
Ok so I just discovered cron and looked at the crontab (/etc/crontab) and found that by default the daily, weekly and monthly jobs are by default set to run at 6:25am, 6:47am and 6:52am respectively.

What happens to these jobs if the meachine isnt on at that time as mine rarely is? Do they get run asap after the machine is turned on or not run at all?

---

### Post by cyracks on 2006-05-10
Nothing they are not executed. Not shure but I think that if you have anacron installed it will also execute cron jobs which were missed.

---

