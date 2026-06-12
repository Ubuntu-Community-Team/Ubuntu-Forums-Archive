---
title: "Add/Remove Applications error"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2007-05-27
When I try to install anything via Add/Remove Apps, I get this message

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by rillip on 2007-05-27
So... did you manually run 

sudo dpkg --configure -a 

?  I believe you'll find it fixes the issue.

---

### Post by amazingtaters on 2007-05-27
ahh yeah forgot the sudo in there. Put that down as absolute retardation. It's all working now.

---

