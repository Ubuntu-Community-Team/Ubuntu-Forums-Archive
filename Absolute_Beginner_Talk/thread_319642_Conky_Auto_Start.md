---
title: "Conky Auto Start"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-16
hi my machine is installed ubuntu 6.06 dapper with KDE 3.5 interface now i am just installed conky now my ubuntu. but when i pc is restart then conky is not start automatically. i run manually. so any way to run the conky with when ubuntu start. :rolleyes:

---

### Post by halitech on 2006-12-16
try checking here

[http://www.ubuntuforums.org/showthread.php?t=205865&highlight=weather]("http://www.ubuntuforums.org/showthread.php?t=205865&highlight=weather")

---

### Post by lucky_chouhan on 2006-12-16
no no no you never understand my problem. i am installed also this link and working fine and check 6 no. point. i am also do this (add in my startup program) but it never auto start.:(

---

### Post by K.Mandla on 2006-12-16
If you add this line to your .xinitrc or your .xsession line, it should start conky when you log in.

```
conky &
```
Make sure you put it before your *exec* line. 

Somebody let me know if KDE does things differently, though. I'm afraid I don't know the KDE setup so well.

---

