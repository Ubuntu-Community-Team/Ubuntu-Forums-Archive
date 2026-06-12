---
title: "Disto info"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by FLEO on 2006-09-29
Hi all,

Just 2 simple questions. 

Is there a command to have full info about the current installed distro ?

If I install dapper over hoary, will the Kernel be update at the same time ?

Thanks,

FLEO

---

### Post by morphodone on 2006-09-29
yes the kernel will be automatically updated

you can go to System -> about ubuntu

---

### Post by Drakkor on 2006-09-29
Or you could put
```
lsb_release -a

```

---

### Post by morphodone on 2006-09-29
> **Drakkor said:**
> Or you could put
```
lsb_release -a

```

awesome, i couldn't remeber that one

---

### Post by Drakkor on 2006-09-30
Yeah,one thing I learned is that you could put ```
history
```in the terminal to find every command you've ever executed, or hit the up arrow and go line by line to see what you've done in the terminal. :p

---

### Post by morphodone on 2006-09-30
wow that's a lot of history...

---

### Post by FLEO on 2006-09-30
sorry guys, I tried lsb_release -a and the command is not found ...

---

### Post by FLEO on 2006-10-01
to be more precise:

I'm running Ubuntu on a server with just command line so maybe that lsb_release command is not installed ...

Tks,

FLEO

---

### Post by FLEO on 2006-10-02
I'm sure there is a command to have the distro info on a command line server. 

I want that because I'm not sure if the update was done correctly.

Tks,

FLEO

---

### Post by K.Mandla on 2006-10-02
You could try uname -a, which shows kernel information and whatnot.

---

