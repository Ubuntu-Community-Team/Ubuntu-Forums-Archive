---
title: "Stopped jobs"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by zappadragon on 2007-03-24
So sometimes when I am working in the terminal and I go to close out I get the "There are stopped jobs" message. What am I doing to cause this? I tried to do a kill and the PID of what it says the stopped job is but it still shows up when I do a ps -u. Is there a better way to clear the stopped jobs?

Thanks

---

### Post by scxtt on 2007-03-24
do you know which jobs are in fact "stopped"? a "T" in the "STAT" column means "stopped" ... are you doing "kill <PID>" only? ... of they're really borked, you may need to do "kill -9 <PID>" ...

---

