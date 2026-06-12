---
title: "process managment"
date: 2010-08-21
forum: Bangalore Team
---

### Post by abhishek.biradar on 2010-08-21
what is the pid for kernel process
and what is the difference between kill and kill -9

---

### Post by msaravanan77 on 2010-10-26
a) what do you mean by Kernel process? are you expecting INIT. PID for init is 1.
b) By defauly kill will send the 'SIGTERM' signal to the given pid. if you use kill -9, this will send 'SIGKILL' signal to the given pid. 
    "kill -l" will list you the all the available signal number with name.

---

