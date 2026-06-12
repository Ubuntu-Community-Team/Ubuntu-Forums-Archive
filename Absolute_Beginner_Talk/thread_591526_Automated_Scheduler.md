---
title: "Automated Scheduler?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-10-25
Is there any way that I can get a scheduler that does certain tasks automatically? For instance, I'd like something that can power down my computer automatically for me at night, or perhaps boot it up for me in the morning the same time I get up. I have other wants too, but is this possible, and if it exists, how can I get it?

---

### Post by kellemes on 2007-10-25
based on [cron]("https://help.ubuntu.com/community/CronHowto") and gnome-schedule.
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html]("http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html")

By the way.. How should cron startup the computer when it's power off? :popcorn:

---

### Post by Onay on 2007-10-25
> **kellemes said:**
> based on [cron]("https://help.ubuntu.com/community/CronHowto") and gnome-schedule.
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html]("http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html")

By the way.. How should cron startup the computer when it's power off? :popcorn:

That's a great point... Just as long as I have the turn off features, since I found that leaving Ubuntu idle for longer than a few hours makes things impossibly jerky, and I end up not being able to shut-down without a hard reset. And yes, I have tried suspend and hibernate, and I can never get my computer out of those once they're in it (I understand that suspend and hibernate have been very hit or miss components of Ubuntu anyway). I'll check it out, thanks.

---

### Post by MegaJim on 2007-10-25
Automated startup is possible through some newer BIOS functions.  If you really need it have a dig around in there.

Its also possible via network using magicpacket or similar

---

### Post by Onay on 2007-10-25
I need help writing a script that allows me to shut down the computer... Here's what I have so far..
```
#!/bin/sh
#
#Shuts down computer

shutdown -P
```
What else do I need to do/revise?

---

### Post by Onay on 2007-10-25
What's the difference between shut down and "shut down and power off"?

---

