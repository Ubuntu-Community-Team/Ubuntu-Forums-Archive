---
title: "Simple cron issue"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by rxtx on 2007-07-22
Hi there-

I'm using Kcron to schedule the running of a simple shell script, but it ...well, doesn't run. Issuing the command via the terminal or desktop is fine, and the commands run happy as, but anything I enter into Kcron doesn't follow through. I've checked crontab and the entries are in there and correct.

Any ideas?

Edit: Sorry- Glossed over this link [ [http://ubuntuforums.org/showthread.php?t=185993&highlight=crontab]("http://ubuntuforums.org/showthread.php?t=185993&highlight=crontab") ]

---

### Post by 5-HT on 2007-07-22
hmmm...Is the crond daemon running? To check:
```
ps aux | grep crond 
```Does the script run as scheduled if you edit your crontab directly?

EDIT: missed your edit. s'working now?

---

### Post by rxtx on 2007-07-23
Ola,

This morning, although I tried a few tests (sucessful) before I went to sleep, cron failed to kick rhythmbox into action and wake me up. Now I'm at work, late with no access to my machine, but I shall give it a check later, could probably swear that cron d is running :confused:

Thanks.

---

