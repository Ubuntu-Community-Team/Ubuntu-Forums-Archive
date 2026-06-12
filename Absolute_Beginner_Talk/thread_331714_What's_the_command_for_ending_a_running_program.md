---
title: "What's the command for ending a running program?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by yuliang on 2007-01-04
It would be useful if I want to make a schedule to both start and end a program.

---

### Post by MkfIbK7a on 2007-01-05
this ends a program in a number of seconds....

sleep <number of seconds> ; kill -9 <process id>

to find process id do

 ps -ax

---

### Post by yuliang on 2007-01-05
Thanks. But it can't be used to schedule a task, because the process ID changes each time the programs run.

---

### Post by MkfIbK7a on 2007-01-05
> the process ID changes each time the programs run.
yes it does, but it can run a task for a certain amount of time once...

---

### Post by 23meg on 2007-01-05
You can use *killall* if you're sure there's only one instance of the program running and that's what you want to kill, but it's not good practice. Also check out *pkill* / *pgrep* and *pidof*.

And in general, kill -9 isn't deemed the ideal way to end processes in scripts. Do a search to find out why not.

---

### Post by MkfIbK7a on 2007-01-05
took your advice and looked it up came up with this replace the -9 with -15

---

### Post by yuliang on 2007-01-05
*pkill* works! The name of the process remains the same all the time.

---

