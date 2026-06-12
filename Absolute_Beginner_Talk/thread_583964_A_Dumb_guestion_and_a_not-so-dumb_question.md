---
title: "A Dumb guestion and a not-so-dumb question"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-10-20
Dumb,
what command tells you which version of ubuntu you are using?

Not-so-dumb:
How do you change the name of the computer? as in- peter@ubuntu:~$

---

### Post by Sef on 2007-10-20
> Dumb,
what command tells you which version of ubuntu you are using?

System > About Ubuntu

---

### Post by p_quarles on 2007-10-20
> **kindafunnylookin said:**
> Dumb,
what command tells you which version of ubuntu you are using?
Open a terminal and type:
```
cat /etc/issue
```

> Not-so-dumb:
How do you change the name of the computer? as in- peter@ubuntu:~$
In the terminal, type
```
gksudo gedit /etc/hostname
```
and change it to whatever you want.

---

### Post by kindafunnylookin on 2007-10-20
Thank you both

---

### Post by Dr Small on 2007-10-20
```
sudo hostname *newhostname*
```
Works too, if I recall correctly.

Dr Small

---

