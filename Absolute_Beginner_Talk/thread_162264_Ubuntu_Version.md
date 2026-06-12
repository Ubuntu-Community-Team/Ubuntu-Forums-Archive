---
title: "Ubuntu Version"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by LiquidFlame on 2006-04-18
This is probably a dumb and simple question, but how do I find out what version of ubuntu I'm running, I know there's some command I can put into the terminal to find out.

---

### Post by GarethMB on 2006-04-18
System > Administration > Software Properties. 

That will give you the version number of your Repos.

You should be able to tell for yourself whether your using Ubuntu or Kubuntu, by the user interface.

---

### Post by xXx 0wn3d xXx on 2006-04-18
[QUOTE=LiquidFlame]This is probably a dumb and simple question, but how do I find out what version of ubuntu I'm running, I know there's some command I can put into the terminal to find out.[/QUOTE]
In termial type:

> uname -a

It will display alot of important info about your system, including the version of Ubuntu that is being used.

Edit: That is just showing my kernel number. Try going under System > About Ubuntu.

---

### Post by nanotube on 2006-04-18
[QUOTE=LiquidFlame]This is probably a dumb and simple question, but how do I find out what version of ubuntu I'm running, I know there's some command I can put into the terminal to find out.[/QUOTE]

in a terminal, type
```
cat /etc/issue
```
and you will see your ubuntu version.

if you want info on your kernel version, then use "uname -a" as suggested above.

---

