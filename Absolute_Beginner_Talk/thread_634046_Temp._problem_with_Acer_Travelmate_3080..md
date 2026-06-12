---
title: "Temp. problem with Acer Travelmate 3080."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Marbash on 2007-12-07
Hello.

I'm running the 7.10 version of Ubuntu on my laptop, and it gets heated up pretty fast. On the driver CD that came with my comp. there is a program package called "Acer Empowering Technology" where I can adjust the CPU from "Low -> Medium -> High -> Max" performance. It's seems that when I'm running Ubuntu, the CPU performance is at Max. Therefore my question is: Is there any program or applictaion that can help me adjusitng the CPU?

---

### Post by Marbash on 2007-12-07
I don't know if this matters. But my processor is a Intel duo core. I've found a program where I can watch the performance, but not adjust it. And the program shows that only one of the "brains" are working. Can this have something to do with my problem?

---

### Post by Marbash on 2007-12-07
Noone knows what to do? =/

---

### Post by handaxe on 2007-12-07
enable manual cpu scaling

```
~$ sudo chmod +s  /usr/bin/cpufreq-selector
``` Then use the cpu panel applet to set your mode. That is, install it by right clicking on the panel and following the obvious instructions.

HA

---

### Post by handaxe on 2007-12-07
Two possibly interrelated things to worry about are

1) whether your install went through cleanly, and 

2) is acpi working? use System monitor to see if acpid is running.

Your cpu should be scaling automatically.  All I wrote was to allow you to manually override the auto settings. In short, something is wrong. 

Try a clean install first if you can.

HA

---

### Post by Marbash on 2007-12-07
The systems seems colder, but I'm not quite sure yet. :) Thanks for the help so far though.

---

