---
title: "Inspiron 600m: powernowd does not start ONLY at boot"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by gevero on 2008-02-23
Hi! I have trouble with powernowd for the frequency scaling of my cpu at boot! It was working fine, then after running powertop it stopped working.

At boot i get the message: **"CPU frequency scaling not supported"** and the system says that the directory **"/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"** is non existent.

If after the boot i run the command **"sudo /etc/init.d/powernowd start"** from the shell powernowd start without anyproblem

so i am guessing that powernowd starts at the boot before the needed directory is mounted or something like that... 

any idea to help me?

thanks a lot!

---

### Post by fuoco on 2008-03-10
Do you still have the same problem?
I had that too and then they fixed the error - but still I powernowd doesn't autostart. I must run sudo powernowd, the initscript doesn't do anything for me....

---

