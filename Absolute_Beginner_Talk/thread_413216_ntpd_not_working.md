---
title: "ntpd not working?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Dertiger on 2007-04-18
I installed ntpd on edgy but it doesn't seem to be running.   In /var/log/syslog, I see these messages every minute or so:

localhost ntpd[22277]: couldn't unlink /var/log/ntpstats/peersta
ts: Permission denied

localhost ntpd[22277]: can't open /var/log/ntpstats/peerstats.20
070419: Permission denied

But "ps aux" confirms that ntpd was run by root and the permissions on the above files and folder are ntp:ntp rw/r/r.

What are these messages telling me?  Is NTP running?

---

### Post by Dertiger on 2007-04-26
I'm still not sure what the problem was, but re-installing ntp-simple did the trick.

---

