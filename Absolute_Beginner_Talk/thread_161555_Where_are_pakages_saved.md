---
title: "Where are pakages saved?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-04-17
Hi,
 I was just wondering where the pakages that I download with synaptic are stored on my harddisk...
Or aren't they stored? Just downloaded, installed and then deleted to make room?
Tx!

---

### Post by jimbz on 2006-04-17
Hi, they are in  /var/cache/apt/archives/. You can delete them with ```
apt-get clean
```

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=jimbz]Hi, they are in  /var/cache/apt/archives/. You can delete them with ```
apt-get clean
```[/QUOTE]
Don't forget to sudo. If you don't use sudo then you will get a permissions error unless you are running as root all the time (which you should not do !). Try this:

> sudo apt-get clean

---

### Post by Ecthelion on 2006-04-17
Ok tx!

---

