---
title: "What is CRON up to?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Fascination on 2007-04-14
I understand what cron is and what it can do, but reading through auth.log I see every so often it throws up:

Apr 15 01:17:01 balamb CRON[7042]: (pam_unix) session opened for user root by (uid=0)
Apr 15 01:17:01 balamb CRON[7042]: (pam_unix) session closed for user root

What is cron actually doing at this point? I cant understand why its needing to open a root session and then close it straight away unless it was checking something? If anyone could shed any light on this, it would be much appreciated. ;)

Many regards,

-Fasc

---

### Post by caffienefree on 2007-04-16
[http://www.splunk.com/base/eventtype:SP-CAAAATZ](http://www.splunk.com/base/eventtype:SP-CAAAATZ)

---

### Post by Fascination on 2007-04-16
Thank you, at least I know *what* its doing now, just need to figure out why! :) I cant understand why it would need to authenticate the root user when no one is logged in though; it seems to be doing it once every hour.

---

### Post by koniczynek on 2007-04-18
I have ubuntu box which is doing exactely the same, every hour @ 17 minutes it launches CRON but the cron entry for this action is nowhere to be found! What's going on? :)

edit: ok, in /etc/crontab there is an entry:
17 *    * * *   root    run-parts --report /etc/cron.hourly
and CRON is doing this every hour @ 17 minute ;)

---

