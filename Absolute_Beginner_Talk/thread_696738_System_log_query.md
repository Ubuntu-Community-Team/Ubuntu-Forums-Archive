---
title: "System log query"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-02-14
since myself and many others are new to linux  and try to understand the system log i'm staring this to ask whatever i want to know about it...like reports,imports e.t.c

---

### Post by someoneouthere on 2008-02-14
i am having this all the time what is it?

```
Feb 14 03:29:35 select-laptop last message repeated 12 times
Feb 14 03:30:35 select-laptop last message repeated 12 times
Feb 14 03:30:37 select-laptop avahi-daemon[5731]: accept(): Too many open files
Feb 14 03:30:40 select-laptop last message repeated 54501 times
Feb 14 03:30:40 select-laptop nufw[5868]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 14 03:30:40 select-laptop avahi-daemon[5731]: accept(): Too many open files
Feb 14 03:30:45 select-laptop last message repeated 114150 times
Feb 14 03:30:45 select-laptop nufw[5868]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 14 03:30:45 select-laptop avahi-daemon[5731]: accept(): Too many open files
Feb 14 03:30:47 select-laptop last message repeated 9146 times
Feb 14 03:30:50 select-laptop nufw[5868]: AUDIT: rx=0 tx=0 track_size=0 list=empty
Feb 14 03:31:25 select-laptop last message repeated 7 times
Feb 14 03:32:30 select-laptop last message repeated 13 times
Feb 14 03:33:35 select-laptop last message repeated 13 times
```

---

### Post by wirelessmonkey on 2008-02-14
It looks like you have the nufw auditing firewall installed.... it's reporting status there.

---

### Post by someoneouthere on 2008-02-28
if someone tries to access my pc via wifi how the log would look like?
any examples/screenshots you might want to share?

---

