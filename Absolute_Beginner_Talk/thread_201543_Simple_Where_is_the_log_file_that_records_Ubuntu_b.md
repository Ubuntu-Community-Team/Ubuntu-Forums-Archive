---
title: "Simple: Where is the log file that records Ubuntu boot?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by fletch on 2006-06-22
Where is the log file(s) that holds the last Ubuntu boot process?

I think I had a bit of an error going on concerning my boot process. Doesn't actually effect my system at all, but it doesn't look healthy and i'm just plain picky and like to stay on the safe side of things.

---

### Post by tonyr on 2006-06-22
/var/log/messages, /var/log/syslog (and other /var/log files)

---

### Post by bikeboy on 2006-06-22
"dmesg" is another good one. Try:```
dmesg | less
``` to be able to scroll through all the hardware detection info from boot time onwards.

---

### Post by fletch on 2006-06-22
Hmm, checked the whole directory, was moreso looking for a log containing exactly what it saids at the startup process. Probably nothing of the sort eh?:confused:

---

