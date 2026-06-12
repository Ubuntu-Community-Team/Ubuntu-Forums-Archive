---
title: "c and java compiler"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by FANGBIN on 2007-01-23
hi everyone,
i wrote some c and java program, but i do not know how to compiler them in ubuntu dapper.
can anyone help out




thanks

---

### Post by taurus on 2007-01-23
```
sudo aptitude update
sudo aptitude install build-essential
gcc **filename.c**
./a.out
```
To compile java program, you need to install java first.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by FANGBIN on 2007-01-23
thanks

---

### Post by macogw on 2007-01-23
For Java, make sure you use javac (the Sun thing) instead of gcj.  GCJ unfortunately is only as up-to-date as Java 1.2, and they just released 1.6.

---

