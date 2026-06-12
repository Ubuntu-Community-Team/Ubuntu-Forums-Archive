---
title: "dpkg: status database area is locked by another process"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by fedrik on 2007-08-09
Now I can't install anything anymore,
I don't know if I'm using synaptic at the same time. Is there any way to find out? How to kill that process?

---

### Post by splintercellguy on 2007-08-09
Something like Synaptic is still running, try donig:

sudo killall synaptic

---

### Post by Pragmatist on 2007-08-09
> **splintercellguy said:**
> Something like Synaptic is still running, try donig:

sudo killall synaptic
You might want to first see if it is running:

```
ps -ef |grep synaptic
```Then, if killall doesn't work, you can do this:
```
sudo kill -9 PID
```where PID appears here:
> 
desktop:~$ ps -ef |grep synaptic
me     **7048**     1  0 09:00 ?        00:00:01 gksudo /usr/sbin/synaptic
root      **7049**  7048  0 09:00 ?        00:00:06 /usr/sbin/synaptic
me     **7873**  6000  0 09:22 pts/0    00:00:00 grep synaptic
In this case I would type:
```
sudo killall synaptic
```and if that didn't work,
```
sudo kill -9 7048
```Then you can check again to see if any more synaptic processes are running, and if so, kill them just like the others:
```
ps -ef |grep synaptic
```

---

### Post by Rocket2DMn on 2007-08-09
I'm not sure killing it like that is safe b/c it might keep holding the lock.  If you can't find it open, you may just want to restart X, or even the whole computer.  Just my 2 cents.

---

### Post by akilian on 2007-08-12
> **fedrik said:**
> Now I can't install anything anymore,
I don't know if I'm using synaptic at the same time. Is there any way to find out? How to kill that process?

Try going into the console(terminal) and typing 
```
dpkg --configure -a
```

---

### Post by bwtranch on 2007-08-12
See my thread How to: Install brother driver DCP 1000 This will show you how to solve the dpkg issue.

---

