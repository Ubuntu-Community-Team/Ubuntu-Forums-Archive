---
title: "sucking up the ram"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by dbvanhorn on 2007-05-09
According to system monitor, something is sucking up my ram.
When I run out of ram, the system hangs.

I never see it use the swapfile, a 3G partition in the boot drive.
At the moment, nautilus has 824M allocated, and 70% of my 2G is used up.
Something seems amiss.

---

### Post by Seisen on 2007-05-09
Type this in the terminal

```
top
``` 

or you can install conky.

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")

Thats how I learned that I was having the same problems and what was doing it.

---

### Post by dbvanhorn on 2007-05-09
Ok, I already know who's eating it, but WHY is the question, and more to the point, what to do about it.

---

### Post by chakkaradeep on 2007-05-09
> **dbvanhorn said:**
> Ok, I already know who's eating it, but WHY is the question, and more to the point, what to do about it.

Who is eating ur system , you didnt mention that :D

---

### Post by dbvanhorn on 2007-05-09
Nautilus, 824M, is by far the worst

---

