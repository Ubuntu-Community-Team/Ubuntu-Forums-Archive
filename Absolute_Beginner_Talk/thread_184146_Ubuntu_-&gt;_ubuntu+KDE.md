---
title: "Ubuntu -&gt; ubuntu+KDE"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by ronlybonly on 2006-05-29
If I use sudo apt-get install kubuntu-desktop in Dapper, can I switch between the two DE's, or will that replace my beloved GNOME with KDE?

---

### Post by zhoux on 2006-05-29
you can switch between KDE and Gnome at the login menu.
I think it is under Sessions

---

### Post by ronlybonly on 2006-05-29
Thanks, zhoux. I just wanted to make sure that I wouldn't mess up my Ubuntu if I installed KDE.

---

### Post by user1397 on 2006-05-29
Wait! Before you do anything, install kubuntu-desktop like this:
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```
this way, you canuninstall it fully later if you want to, but if you do this with apt-get, you'll have to uninstall all the KDE programs manually using synaptic or a command line.

---

### Post by aysiu on 2006-05-29
erik1397 is right.

Here are full instructions:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

