---
title: "starting second x session"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Nolander on 2008-01-18
Im trying to start a second xsession, this [thread]("http://ubuntuforums.org/showthread.php?t=185555"). But when i run:
```
startx --:1
```
i get:
```
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

```
should i do wat it tells me to do?

-nolander

---

### Post by Cypher on 2008-01-18
Any particular reason you are trying to run 2 xsessions at the same time?

The command might work if you try
```

startx -- :1

```

---

### Post by Nolander on 2008-01-18
thanx that worked and i dont know y? y does any one do ti?

---

