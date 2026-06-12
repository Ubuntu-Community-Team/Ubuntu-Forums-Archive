---
title: "how to see a list of whats running?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by HMartinho on 2007-10-29
Whats the task manager equivalent in Ubuntu, for example if something has gone wrong how can I "Ctrl+Alt+Del" to select wich process to kill?

Thanks in advance.

Cheers.

---

### Post by skymera on 2007-10-29
go to terminal and write:

top - too see what is runnign

system>admin>system monitor 

thats what u looksy for :D

---

### Post by oilchangeguy on 2007-10-29
> **HMartinho said:**
> Whats the task manager equivalent in Ubuntu, for example if something has gone wrong how can I "Ctrl+Alt+Del" to select wich process to kill?

Thanks in advance.

Cheers.

you can go to system, system monitor, processes.

---

### Post by stanigator on 2007-10-29
You can also do this in terminal if you know what process is not responding:

```

ps waux

```

to see all the processes running

```

ps waux | grep "non-working application"

```

to see the applications with the name of the non-responding application

then apply
```

kill -9 process-number-of-non-responding-application

```

to kill the process in terminal.

---

### Post by sailor2001 on 2007-10-29
system/administration/system monitor/processes

---

### Post by HMartinho on 2007-10-29
Thank you both/"all" very much. (I had two replies before replying myself ;))
By the way, talk about fast help!! :)

Cheers.

---

### Post by Cochise on 2007-10-29
open a terminal and type ps -ax

---

