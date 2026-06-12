---
title: "Where is the system log?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-04-21
Where is the system log?

---

### Post by Rinzwind on 2007-04-21
/var/log
all logs should be there.

also see
system/administrarion/system log.

---

### Post by altaaa on 2007-04-21
in /var/log/messages.

to view it, open a terminal and type in one of the following:

```
cat /var/log/messages
```

```
less /var/log/messages
```
This one you can scroll in, exit by pressing q

You can view your boot log by entering this in a terminal:

```
dmesg
```

```
dmesg | less
```
Again, with scrolling.

---

