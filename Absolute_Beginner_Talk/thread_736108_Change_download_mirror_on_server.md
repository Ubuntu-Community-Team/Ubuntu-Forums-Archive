---
title: "Change download mirror on server?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by boardtc on 2008-03-26
Working with gutsy server, the Ubuntu download mirror picked up by aptitude is currently down. How can I change this mirror so I can keep downloading packages?


Thanks Tom.

---

### Post by hyper_ch on 2008-03-26
edit /etc/apt/sources.list and alter it... normally the repos are prepended with a country abbreviation... you may alter it on your desktop, see what changes it made to the sources.list and apply that to your server...

---

### Post by oedha on 2008-03-26
go to system - administrator - software sources
mark on source code box and change the main server to your nearest server
if you know the server already....you can do like what hyper told you :)

---

### Post by boardtc on 2008-03-26
magic. thank you.

---

### Post by boardtc on 2008-03-26
> **oedha said:**
> go to system - administrator - software sources
mark on source code box and change the main server to your nearest server
if you know the server already....you can do like what hyper told you :)

i'm running server, thanks, sorted now.

---

