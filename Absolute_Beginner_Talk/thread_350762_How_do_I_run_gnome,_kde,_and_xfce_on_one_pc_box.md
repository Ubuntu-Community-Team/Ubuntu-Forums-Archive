---
title: "How do I run gnome, kde, and xfce on one pc box?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by kurisutofuaa on 2007-02-01
I have been wondering if this is possible to do and how you would go about doing it. :guitar: 

It's just something that I think would be cool.

---

### Post by r4ik on 2007-02-01
sudo aptitude update && sudo aptitude install xubuntu-desktop

For KDE,

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by JustKDE on 2007-02-01
To install KDE type the following in the terminal:

```
sudo apt-get install kubuntu-desktop
```And also for Xfce:
```

sudo apt-get install xubuntu-desktop
```To switch between them use the Options button on the login screen.

---

### Post by kurisutofuaa on 2007-02-01
So what is the difference using *sudo apt-get* and *sudo aptitude*?

---

### Post by floke on 2007-02-01
See this

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by hyper_ch on 2007-02-01
aptitude can handle meta-packages such as xubuntu-desktop and remove all of its component that aren't required anymore (if you decide to deinstall it again)... apt-get can't do that.

---

