---
title: "Synaptic 'what is popular'"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2005-08-11
is there any way of finding out which packages are the most popular in synaptic? perhaps I am missing out on some groovy stuff  :smile:

---

### Post by SGC on 2005-08-11
16986 ubuntu packages ordered by thier popularity, Page size: 1.62 MB:
[http://popcon.ubuntu.com/by_inst](http://popcon.ubuntu.com/by_inst)

---

### Post by Sam on 2005-08-11
To activate the popularity context on your box (which is not enabled by default IIRC), type in a terminal:
```
$ sudo dpkg-reconfigure popularity-contest
```
It'll send to the Ubuntu server once a week the packages you use.
For more information:
```
$ man popularity-contest
```

---

### Post by pompeyjohn on 2005-08-12
Whoa thats a big old list!! It is going to take some time to work through that and find the applications amongst the system packages. As good a place as any to start. Thanks for the list, and the pop context command  ;-)

---

### Post by UbuWu on 2005-08-12
The popcon page hasn't been updated for the last two months...  :mad:

---

