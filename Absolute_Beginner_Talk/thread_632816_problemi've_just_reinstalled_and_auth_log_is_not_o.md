---
title: "problem:i've just reinstalled and auth log is not on system log why?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-05
problem:i've just reinstalled and auth log is not on system log why?

---

### Post by kelbizzle on 2007-12-05
Try issuing this command..
hit alt+f2 then type 
```
gksudo gedit /etc/X11/xorg.conf
```

It should prompt you for a password after which check the log to see if the authlog is there. If not just click on open. Goto /var/log and select auth.log.

---

