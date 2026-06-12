---
title: "Debugging - boot up stopped ..."
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-30
Yesterday I installed Samba.  I am running Gutsy.  This morning, on boot up, my screen went into full screen text mode showing the processes that were trying to start.  The boot up process stopped at a line "Starting Samba daemons".  I noted that this was the /etc/rc2.d/S20samba.  So, knowing nothing better to analyze why this happened, I just renamed S20samba to xxxS20samba.

My question, is there a better way to fix this and analyze why this happened?  Log files, etc?

Carl

PS:  I had to also rename S20winbind to xxxS20winbind to get Gutsy to fully boot.

---

### Post by nick_h on 2007-10-30
There is a log file viewer under System->Administration->System Log.
Is there anything in /var/log/messages, /var/log/syslog or /var/log/kern.log ?
dmesg would be the first place to look.

---

