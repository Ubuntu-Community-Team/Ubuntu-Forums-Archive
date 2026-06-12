---
title: "how to know if a process is alive"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by herbert tamayo on 2008-01-22
Hi, I need to know if mysql and apache -for example- are running, if I do ps -all it will list me all the process that are running, but is there a way to know if mysql, apache or other process is running?

An example:
some_monitor_command mysql
some_monitor_command apache


Second question:
Sometimes I use more than one session at the same time, for example graphical mode, tty2 (using Alt+F2), tty3 (Alt+F3), so, I do everything I need in tty3 for example, my question is:

Once I finished to use tty3 is there a way to kill tty3? if I go to tty2 and I do a ps -all I can see the process in tty3, so I want to kill all the tt3, can you help me?

---

### Post by njparton on 2008-01-22
```
top | grep -i mysql 
```

should work

---

### Post by stump138 on 2008-01-22
you can also try
```
ps aux | grep -i mysql
```
:)

---

