---
title: "System Crashed!"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by meniscus on 2007-01-25
My system crashed there yesterday.  I was doing nothing out of the ordinary. Does ubuntu log this anywhere or does it log the reason as to why the system crashed?

---

### Post by taurus on 2007-01-25
May want to have a look in /var/log/messages.

```
sudo tail -30 /var/log/messages
```

---

