---
title: "How do you control who run a particular program at startup?"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-07
Assuming I have this script called 'testscript' in /etc/rc2.d/ 
```

/etc/rc2.d/S20testscript -> ../init.d/testscript

```

Is it possible for 'testscript' to run as USER 'userA' instead of 'root' at startup, so that if I do a 'ps aux', I'll get

USER  PID  %CPU  %MEM  VSZ RSS TTY STAT START TIME COMMAND
----------------------------------------------------------------------
userA 6334  0.0  0.5   443 443  ?   Ss  06:20 0:00 /usr/bin/testscript
  ^
  |
userA instead of root here
(which is shown correctly above)


Thanks.

---

### Post by [2]BoxingFiend on 2006-02-07
if inside testscript you use sudo to execute as userA

---

