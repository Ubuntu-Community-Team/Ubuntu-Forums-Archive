---
title: "Repository not available"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by saby4237 on 2007-09-13
While trying to check for updates in Update Manager, the following error is occurring:
[ATTACH]43362[/ATTACH]

Can anybody please help?

---

### Post by justleen on 2007-09-13
did you add any sources your sefl to the repository list?


```
 # sudo gedit  /etc/apt/sources.list 
```
look for the url that is failing, and comment it out (place a # in front of the line)
run am apt-get update afterwards

---

### Post by saby4237 on 2007-09-13
Thanks A LOT justleen for replying. 
A few minutes back I could resolve the problem. I chose  System > Administration > Software Sources     and changed my software source to the Ubuntu Main source.

 Seems my earlier local source had its server down or something. 

Anyway, Thanks again bro!

---

