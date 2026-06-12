---
title: "Is syslog always restart on its own?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by christelle_cabubas on 2007-06-04
Hi,

Just wanna ask if you could help me on this. We have this kind of server which monitors all our equipment 24x7 (365 days a year)..but we cannot push through with this project because it always hang-up. At first we thought its the sql database that causes the hang-up and did a repair on it. But after 2 weeks it get crashed again. Again, we have to restart the device since it can no longer access via putty (a telnet software)..did a a little repair again on the database...etc..etc..

Until we found out something about its logs at /var/log/messages. Syslog always restart on its own at around 6:47am everyday..some are successfully loaded even its sql database but sometimes it failes to back on its normal status and causes sql database to crashed down. I wonder is this really happens?i mean syslog automatically restart on its own.any suggestions?..really appreciated it so much..

thanx,

chris

---

### Post by dstew on 2007-06-04
Please post the messages file. If you see a line that says <date> <time> computername syslogd <version>: restart, that means that the system has been restarted, not just syslogd. It sounds like you might have a power  problem or something else that causes the system to restart.

---

