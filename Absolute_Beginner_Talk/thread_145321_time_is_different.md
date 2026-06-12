---
title: "time is different"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by aquilegia on 2006-03-16
My windows xp time and ubuntu time is different..
Why?

---

### Post by jasay on 2006-03-16
[QUOTE=aquilegia]My windows xp time and ubuntu time is different..
Why?[/QUOTE]
Linux sets the hardware clock to UTC and calculates local time based on your timezone where windows stores local time to both the hardware and system clocks.  To make ubuntu time match windows time you should right click the clock on the panel, goto preferences and deselect UTC.

---

### Post by mcduck on 2006-03-16
[QUOTE=aquilegia]My windows xp time and ubuntu time is different..
Why?[/QUOTE]
Unix systems, like Linux, usually use GMT as the system time, and then use your time zone information to show you right time. I think there was option during install to choose to run your system clock in local time.. I'm not sure how to change that after install, but I'll see if I can find something :)

---

### Post by mcduck on 2006-03-16
well, jasay already replied with the easy way. But if that doesn't work,here's another way:

Open terminal and run 'sudo gedit /etc/default/rcS'. Now find the line with 'UTC=yes' and change that to 'UTC=no'. Save and restart your machine. Set the time and timezone if you need and your problem is gone :)

---

