---
title: "CPU usage says 91%id?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by dkmp on 2008-02-13
Hey,

I'm new to ubuntu and wondering about my cpu usage.

As soon as I boot into ubuntu my cpu usage goes through the roof. It does not happen when I use xp.

It ranges from 85-95%. When I use system monitor no process is shown that is using this much power but when i use TOP I see that CPU id is using 90% of this. What is this? Can it be fixed?

Thanks

D

---

### Post by oilchangeguy on 2008-02-13
> **dkmp said:**
> Hey,

I'm new to ubuntu and wondering about my cpu usage.

As soon as I boot into ubuntu my cpu usage goes through the roof. It does not happen when I use xp.

It ranges from 85-95%. When I use system monitor no process is shown that is using this much power but when i use TOP I see that CPU id is using 90% of this. What is this? Can it be fixed?

Thanks

D

computer specs please.

---

### Post by dkmp on 2008-02-13
Hey,

intel centrino 1.73 Ghz. ram 512mb , HDD 80gb (laptop). graphics card 128mb shared

Thanks

---

### Post by copperco2 on 2008-02-13
I am too having a similar problem, my laptop gets heated too much, slows down and gets shut down due to it..

its a celeron 1.6, 512 ram, 40gb hdd i am using ubuntu 7.10

---

### Post by dkmp on 2008-02-13
Yeah, its weird whats eating up the processor but its not listed in the processes.

Maybe i'll just go back to using good old xp!!!!!!!!!!!!!!!!!!!!

D

---

### Post by cawill on 2008-02-13
You might have done this but, have you selected view > all process?

---

### Post by plucky on 2008-02-13
>  CPU usage says 91%id?


Doesn't that mean **idle**?

---

### Post by schiznik on 2008-02-13
Youre looking at this line in top, correct?
```

Cpu(s): 0.3%us, 0.3%sy, 0.0%ni, 97.7%id, .... etc
```
This is the % that is idle, similar to the System Idle Process in Windows' Task Manager.```
man top
```will explain more - its in section "2c. CPU States" in the debian manpage, I dont have access to an ubuntu system at the moment, but I expect that its the same.

---

### Post by copperco2 on 2008-02-13
is idle a process?
and if it is showing that much..above 90 and still the laptop is getting hot and as a result tje machine shuts down...
then what will be the possible solution or is there no solution?

---

### Post by plucky on 2008-02-14
> is idle a process?

**Yes** ,It is what your computer does when it has nothing else to do.

> what will be the possible solution or is there no solution? 

Time for some basic maintenance i.e a good cleaning and make sure the fans are working.
Either do it yourself if you know how,or take it to local computer shop who will do it for a large fee.

Good luck

---

### Post by hyper_ch on 2008-02-14
instead of using top I prefer htop:

```

sudo apt-get install htop

```

```

htop

```

---

