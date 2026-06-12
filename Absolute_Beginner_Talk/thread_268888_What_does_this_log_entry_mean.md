---
title: "What does this log entry mean?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by crokett on 2006-09-30
Checking my logs and I see this logged in /var/log/messages.  It is repeated several times a day.  

Sep 27 19:16:13 Hawking -- MARK --
Sep 27 19:36:14 Hawking -- MARK --

Google did not turn anything up.  It gets repeated every 20 minutes.   I checked crontab but did not see anything there either.

---

### Post by Miademora on 2006-10-01
"This is the syslog daemon marking off time intervals to show in the logs that the system itself and also the syslog daemon were alive at this time."

---

### Post by MKR. on 2006-10-01
To expand on that: That mark tells you the last time the system was working in the event of a system failure. It helps you narrow down the cause of a problem. :D

---

### Post by crokett on 2006-10-01
Thanks fellas - I got the same answer over on justlinux.  I don't like seeing things in the system logs when I didn't tell the system to do whatever it is logging.  I will check the syslog.conf file - maybe edit the message to something more descriptive.

---

