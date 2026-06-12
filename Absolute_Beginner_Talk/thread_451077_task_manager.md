---
title: "task manager?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Alusair on 2007-05-21
I keep getting this error whenever I try to use the package manager and/or add/remove programs function.

```
Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
```

Is there a task manager similar to task manager in windows that caan show me what processes are running and give me the option to kill them off?


--------------
Kubuntu 7.04 Fiesty Fawn x86_64 on HP Pavilion dv8100CTO

---

### Post by n8bounds on 2007-05-22
you can only run aptitude once at a time

running aptitude can be counted as doing any of the following:

-sudo apt-get whatever from a terminal

-running updates

-running add/remove

-maybe some scripts (Automatix)

-automatic secuirty updates could be running in the background

you may simply have a stale pid file, to remove say this in a terminal:

sudo rm /var/lock/aptitude

(I think)

---

### Post by aysiu on 2007-05-22
Try Alt-F2 ```
ksysguard
``` But, yeah, you can't have more than one of the following running at once: Update Manager, Adept Package Manager, *apt-get*, *aptitude*

---

### Post by richaoj on 2007-05-22
btw, just for general help, there is a gui task manager in 
System> System monitor

---

### Post by aysiu on 2007-05-22
> **richaoj said:**
> btw, just for general help, there is a gui task manager in 
System> System monitor
Is that the path in Kubuntu, too?

---

### Post by richaoj on 2007-05-22
d'oh . . . i should read more carefully .

---

