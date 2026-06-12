---
title: "cron alarm?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by onlythetim on 2006-12-20
I would like to use my computer as an alarm clock, so I thought I would just use crontab with xmms to play a song when I wake up, so I did **crontab -e** and added the line
**30 14 * * * xmms /music/Metallica/Master_of_Puppets**

However, this doesn't work.  I used 2:30 pm as the test time, and waited for it to role around.  But when it did, nothing happened.  Am I doing something wrong here?  Why isn't this working?  Is there a better way of accomplishing the same thing?

Thank you.

---

### Post by idrinkwhisky on 2006-12-21
i have Xmms and i downloaded some alarm plugin and it works.
in xmms go to options --> preferences --> general plugins.

there should be a plugin called "alarm 0.3.7 libalarm.so
click it and click configure.

hope it works for you

---

### Post by munkar on 2007-01-12
in case you'd prefer to use cron, as i do....

the reason that nothing shows up is that you need to do export DISPLAY=:0.0 before calling XMMS. i have no idea what it does, but it works. also, cron wants you to specify the path of XMMS. here is my crontab file (called scheduled.tasks):

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# to reset crontab, do:
# crontab -r && crontab ~/my/data/scripts/scheduled.tasks && crontab -l

# m h  dom mon dow   command
30 6 * * * ~/my/data/scripts/morning.alarm  # alarm for 6:30am

```

here is the script invoked by the crontab entry (morning.alarm). i'm still trying to figure out how to get it to set XMMS' volume as well as the main volume:

```
#!/bin/bash
# script to run alarm in xmms in the morning

amixer set Master unmute # unmute master volume 
amixer set Master 20     # set master volume to 20 (65%)
# FIXME: need to set xmms volume as well

# run alarm.mp3 in xmms
export DISPLAY=:0.0   # needed to run X-based programs
/usr/bin/xmms ~/my/mp3s/alarm.mp3

# log successful execution (by cron, usually) in alarmlog
date >> ~/Desktop/alarmlog
echo "alarm file run" >> ~/Desktop/alarmlog

```

---

