---
title: "uptime says 2 users"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-03-12
I was looking up my uptime and noticed that it says "2 users"!

Does that mean there are 2 users logged into my computer?  Because I only have 1 user and 1 root.

Can more than 1 user be logged in?

---

### Post by Mr. C. on 2007-03-12
Yes, multiple ssh logins or terminal logins will appear as multiple users in uptime.

```
ps -ef | grep bash
```

also try:

```
last
```

MrC

---

