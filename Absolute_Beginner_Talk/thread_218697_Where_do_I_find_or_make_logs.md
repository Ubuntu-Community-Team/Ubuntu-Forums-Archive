---
title: "Where do I find or make logs?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Sammi on 2006-07-18
Often times I encounter a problem, which makes me want to review the output that the application in question makes. Mostly that which it spews out on the terminal. Is this data usually saved anywhere specifically or do I have to do something first in order for it to "record" the console output?

One example scenario where this would be useful:
I have been playing a bit with Compiz/Xgl, and every now and again it breaks, because of updates and various other changes, so that when I try to initialise it it can crash my whole X server. This is frusterating because it makes it impossible for me to read the output from the commands I made when starting Compiz, because the crash happens before I get just a glimpse of the output.

---

### Post by Cyraxzz on 2006-07-18
**System > Administration > System Log**

---

### Post by scxtt on 2006-07-18
there's an entire directory of logs --> **/var/logs/** and you can view them easily using what Cyraxzz posted (but you have to load them initially) ...

---

### Post by Sammi on 2006-07-18
Thanks!

But which of all those logs are relevant? I mean there are so many... help file says: messages, Xorg.0.log, user.log, and syslog. But are there any more logs that are good to monitor?

---

