---
title: "make: Command not found"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2005-12-06
this is so frusterating! I was attempting to compile nmap from source but after I ran the config script, "make" doesn't work! The console returns command not found. What can I do to fix this problem?

---

### Post by sapo on 2005-12-06
just type on a terminal:

```
sudo apt-get install automake
```

it should do the trick.

---

### Post by wr0x2 on 2005-12-06
I did that, and it seemed to install automake, but the make command STILL doesn't work.

---

### Post by m0biu5 on 2005-12-06
The only thing I can think of is to get the compliation tools (build-essential) from apt.

---

### Post by wr0x2 on 2005-12-06
Thanks m0biu5! I installed the build-essential and make works now.

---

### Post by m0biu5 on 2005-12-06
Awesome, glad I could help.

---

