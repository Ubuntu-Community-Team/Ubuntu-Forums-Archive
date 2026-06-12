---
title: "Another Process is using root from startup..."
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-10-21
I am running Kubuntu.

I started my laptop and I wanted to download a program. I went to adept and it gave me something that said that another process is using root and I need to end that process before using Adept. 

What command will show me my processes so I can post them here to fix this problem?

---

### Post by taurus on 2006-10-21
Open a terminal and type

```
ps -A
```
Then, look thru that list to see perhaps synaptic or something similar is running in the background.  Kill it with the "kill -9 PID" command.

---

### Post by tdrusk on 2006-10-21
I fixed it. User error lol.

---

### Post by taurus on 2006-10-21
Open a terminal and try it with aptitude

```
sudo aptitude update
sudo aptitude install <your program>
```

---

