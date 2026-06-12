---
title: "How do i edit files?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by James42 on 2007-06-23
I just started using Ubuntu 7.04 a couple days ago and I've started to get the basics to using it. But when I'm trying to install some things they ask me to edit a certin file like(/etc/apt/sources.list). 
How do i go about doing that exactly? I would appreciate any help

---

### Post by Outrunner on 2007-06-23
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by James42 on 2007-06-23
thanks alot.

---

### Post by Phixion on 2007-06-23
gedit is one way, you can also use nano or vim, just depends on your preference.

---

### Post by James42 on 2007-06-24
whats the difference between the 3?

---

### Post by punx45 on 2007-06-24
gedit is graphical.   the other two are invoked on the command line (and may or may not have graphical front ends as well.)

i suggest learning at least basic use of vi/vim just in case you ever need to use it someday (e.g. editing files on a remote server, or fixing an X.org meltdown)

plus, anyone that edits with vi is instantly cooler. :)

---

