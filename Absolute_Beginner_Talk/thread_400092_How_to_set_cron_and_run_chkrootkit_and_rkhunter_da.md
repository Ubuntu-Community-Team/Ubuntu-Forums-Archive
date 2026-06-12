---
title: "How to set cron and run chkrootkit and rkhunter daily?"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Beamvr6 on 2007-04-03
Hi,

I keep a practice of running chkrootkit and rkhunter on a semi regular basis (nothing suspicious until now) and now want to setup cron so both run every day and (if possible) only give a signal when it finds something suspicious. Or a brief summary would also be fine.

I am totally new to cron and I've been searching the forums and found quite some posts but feel unsure how to set it up. I mean which lines, commands, parameters etc.

TIA

---

### Post by irwa82 on 2007-04-04
Hi,

The easiest way is to put a script into /etc/init.d/cron.daily/ directory. Anything in that directory will be run every day.

you can make a small script like below:

-----------------------------------------
#!/bin/sh
/command/to/execute/here
-----------------------------------------

make sure you set the file permissions too:

sudo chmod 755 /etc/cron.daily/yourscript.sh

---

### Post by Beamvr6 on 2007-04-05
OK, did some investigation and there is both a chkrootkit and a rkhunter script in /etc/cron.daily already. Also a rkhunter.log in /var/log on 2 consecutive days now. I think it the scripts were installed whit both utilities? 

Anyway my question is not so much cron related now, more like how to set chkrootkit and rkhunter in a way both produce a summary without the need to check the entire logfile everyday.

A learning Ubuntu user.

---

