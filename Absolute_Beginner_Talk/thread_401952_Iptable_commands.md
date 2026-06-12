---
title: "Iptable commands"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by hardipdhillon on 2007-04-05
How can i list applied iptable commands,i have used iptable -L but this one doen't list the iptable command that i applied

---

### Post by Jussi01 on 2007-04-05
Is there a reason you want the commands? firestarter is the gui front end for iptables. however if you do 

```
man iptable
```

that should give you some hints.

---

### Post by hardipdhillon on 2007-04-05
I have checked in man page it give -L option for listing but that one is not working

---

### Post by hardipdhillon on 2007-04-06
can any body help me

---

### Post by Austin_KW on 2007-04-06
sudo iptables -L

---

### Post by hardipdhillon on 2007-04-06
when i run this command it only shows the headings not the actual command,i can't see the command that i have applied,did that mean i my iptable command hasn't been applied

---

