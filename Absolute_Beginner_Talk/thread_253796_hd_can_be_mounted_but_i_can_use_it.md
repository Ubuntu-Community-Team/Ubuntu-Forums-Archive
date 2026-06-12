---
title: "hd can be mounted but i can use it"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by JohnnyMi25 on 2006-09-08
iv got an external hd that (was working perfectly fine 2 days ago) can be mounted but when i try to look  at files on it (go into it) it says: "Could not enter folder /media/drivename"

where should i start?:confused: e

---

### Post by bswilson on 2006-09-08
The first step is to share with us here the output of the mount command, so we can see what options your drive is mounted with.  It may be mounted as read only.  Try:

```
mount |grep drivename
```

---

