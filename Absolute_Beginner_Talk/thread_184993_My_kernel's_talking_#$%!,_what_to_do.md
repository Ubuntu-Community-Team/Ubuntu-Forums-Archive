---
title: "My kernel's talking #$%!, what to do?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-05-30
I usually do a little audit once a week, you know, update the tripwire database, read the system mail, and look through the logs.  This week, I'm dying:

From syslog:

```

May 30 00:15:23 host kernel: [4303449.260000] Uhhuh. NMI received for unknown reason 31 on CPU 0.
May 30 00:15:23 host kernel: [4303449.260000] Dazed and confused, but trying to continue
May 30 00:15:23 host kernel: [4303449.260000] Do you have a strange power saving mode enabled?
```

And from kern.log:

```
May 29 11:24:44 host kernel: [4294673.675000] Driver 'sd' needs updating - please use bus_type methods
```

What up, kernel?  Chickety check yourself, beeyatch.

Can someone explain this to me?  I'm particularly interested in knowing more about the kern.log message.  How do I get this driver using bus_type methods?  What is bus_type methods?  It looks udevvy...oh, and my udev log is a disaster area as well.

runny

---

### Post by gr83 on 2006-08-16
Aaaah I'm having the same issue on a new system :-k

---

