---
title: "Process priority"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by jonny123 on 2006-12-13
Hi
I have compiled from source code, running a program which hogs 
cpu time when in demand, I need to limit or lower priority to 
the daemon. 

I can't find it in system monitor, it runs in /var/run/    
audsld.pid
audsld.shmid

I can easily terminate it by kill command.

Jon

[http://www.araneus.fi/audsl/](http://www.araneus.fi/audsl/)

---

### Post by bollix47 on 2006-12-13
Have you tried using the [_nice_]("http://www.ss64.com/bash/nice.html") command.

---

### Post by jonny123 on 2006-12-13
That's new to me, can you give explaination / examples?
Thx Jon

---

### Post by jonny123 on 2006-12-13
nice /var/run/audsld.pid : permission denied.
logged in as root, and also su. :(

---

### Post by bollix47 on 2006-12-13
Try nice -19 /path/to/command

pid files are process identification files, not command files.

You have to use the nice command where you start this program that you compiled from source.

---

### Post by jonny123 on 2006-12-14
It runs the program with no output errors, I would like to check on it in system monitor / top but it is not shown there, how can I reveal the process, how can I monitor the PID process etc. cheers

---

### Post by jonny123 on 2006-12-14
Don't worry found it by 'list all' in system monitor
(how silly of me.)

Thx for your help.

---

