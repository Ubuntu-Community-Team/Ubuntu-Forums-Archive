---
title: "kill ?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by _Oleg_ on 2008-03-31
[INDENT]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/INDENT]

after reading forum i found that current session not closed

[INDENT]
 ps -e | grep -e apt -e adept | grep -v grep
 4404 pts/0    00:00:00 apt-get
[/INDENT]

i am tring to kill (kill 4404) it not seams without any sussex..

how to kill it?

---

### Post by munkyeetr on 2008-03-31
Check to make sure you don't have either the Synaptic Package Manager or the Add/Remove Programs window open at the same you are tryin to run apt-get on the comand line. They all pull form the same place, so you'll get a resource conflict.

---

### Post by _Oleg_ on 2008-03-31
i am running it without X windows, its a server.. and yes i have it running... how to stop it?

---

### Post by munkyeetr on 2008-03-31
I would try:
```

sudo kill 4404

```

does that work, if not what output do you get, if any?

---

### Post by _Oleg_ on 2008-03-31
it doesn't show any response and doesn't kill process =(

---

### Post by munkyeetr on 2008-03-31
sorry, I don't know then, offhand. wait for someone else to come along, who may have another idea...

---

### Post by munkyeetr on 2008-03-31
can you post the output of:
```

ps x

```

---

### Post by munkyeetr on 2008-03-31
try running:
```

sudo killall apt-get

```

---

### Post by kbless7 on 2008-03-31
In the terminal run

```
ps -aux
```

This will bring up a list of running processes. Then run

```
kill -9 pid
```
or
```
kill -15 pid
```

The pid is the process ID that you get from the ps -aux command.

---

### Post by _Oleg_ on 2008-03-31
kbless7, god send you to me!

thank you!

---

