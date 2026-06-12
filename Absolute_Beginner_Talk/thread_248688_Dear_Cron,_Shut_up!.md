---
title: "Dear Cron, Shut up!"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-09-01
How can I stop cron from emailing my username every hour on the hour to tell me that what it's running?

It doesn't affect me too much, but everytime I log in to the command line it tells me I have mail and I feel the OCD need to check it and delete it.

I'd just as soon disable mail for my user account all together if that's possible since it's a single user system and I don't use it for anything else.

---

### Post by Nytram on 2006-09-01
add
>/dev/null
after the command name in your crontab jobs list

---

### Post by pbaehr on 2006-09-01
That makes sense.

I've added it to my one cron entry, however this brings me to a second question. There is something running hourly that I can't track down. Every hour on the hour, something, somewhere runs a "test -x" command to check up on a file. There is nothing but a placeholder file in /etc/cron.hourly and neither my crontab nor the root crontab contain anything that would be running with that frequency. Is there anywhere else I can look for this command? I'd like to at least know what it is that's running.

---

