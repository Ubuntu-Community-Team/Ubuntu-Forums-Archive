---
title: "automatic update to the lastest package"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by linuxcity on 2006-05-04
I'm running Dapper and I have to manually run update several times a day (I like to get the latest package available).

How do I set it so that it automatically checks for update every # of hours?

---

### Post by _simon_ on 2006-05-04
You can only do it: Daily/Every 2 Days/Weekly/Every 2 Weeks.

System -> Administration -> Software Properties -> Internet Updates

---

### Post by linuxcity on 2006-05-04
I don't see the "Sotware Properties" under System-Administration? Do I need to add it manually or it is missing from my system?

---

### Post by _simon_ on 2006-05-04
try this from terminal instead

```

gksu /usr/bin/software-properties

```

---

### Post by linuxcity on 2006-05-04
I tried that, but nothing happened.

---

