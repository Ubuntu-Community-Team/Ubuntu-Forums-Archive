---
title: "Kill a program that is not responding."
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2006-11-21
"Firefox is running but not responding" How do I kill a program that is not responding in Ubuntu? Thanks.

---

### Post by dbott67 on 2006-11-21
Open a terminal & type in:
```
ps aux | grep firefox
```
The output will display a PID# (i.e. 3156)
Type in:
```
kill -9 3156
```

-Dave

---

### Post by illu45 on 2006-11-21
If you're using Gnome, the easiest way is probably to go to System -> Administration -> System Monitor -> Processes -> Select firefox-bin -> Click End Process. 


Hope that helps,
illu45

---

### Post by ewl1217 on 2006-11-21
Press Ctrl+Alt+Esc and you should get a skull cursor. Left-click on the program that you want to terminate. Right-click to return to a normal cursor.

---

### Post by bodhi.zazen on 2006-11-21
> **jmtjet said:**
> "Firefox is running but not responding" How do I kill a program that is not responding in Ubuntu? Thanks.

In a terminal type "killall <application_name>

In this case:```
killall firefox
```

If you do not know the name:```
ps -aux
```Will list all running applications.

Kill by number (PID) or killall by name.

---

### Post by LLRNR on 2006-11-21
Or Ctrl+Esc => you'll get a list of running processes, select the unresponsive one and choose "Kill".

---

### Post by jmtjet on 2006-11-21
WOW, that was fast. Thanks all, I've got it killed. :)

---

### Post by xpod on 2006-11-21
Well mabey a bit simpler but i`ve found just rapidly clicking the box to close any frozen apps usually brings up a "force quit" option.

Of course theres all the "proper" ways these guys mention:)

---

### Post by TheRingmaster on 2006-11-21
was it bloody?

---

### Post by jmtjet on 2006-11-21
> was it bloody?

No, neary a drop was spilled. :)

---

