---
title: "crontab"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by noone123 on 2007-03-30
hi, i wanted to make a cronjob to a .pl script but the script doesn't run... whit the crontab script(the line in crontab file) is everything ok and whit the .pl script too. The thing is that i think the crontab file isn't running at the right time or any time. I think so because i used the same cronjob line before i reinstalled my ubuntu. Maybe theres something else? by the way, im not using Gnome but FluxBox(this could be useful).

---

### Post by raja on 2007-03-30
Which crontab did you add it to. I have had similar problems with the user crontab. Worked ok after I added it to /etc/crontab.

---

### Post by noone123 on 2007-03-30
i also added to /etc/crontab.
Hey... i found some error... when i type cron(just cron in putty) its says this:

[PHP]cron: can't lock /var/run/crond.pid, otherpid may be 9747: Resource temporarily unavailable
[/PHP]

---

