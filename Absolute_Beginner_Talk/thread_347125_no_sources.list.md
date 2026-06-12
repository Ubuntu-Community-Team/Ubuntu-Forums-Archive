---
title: "no sources.list"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-01-26
well im trying to upgrade to edgy and im trying to fix my source list which seems to gone now.  i cant even save a new one because it says the file does not exist.  what do i do now?

---

### Post by taurus on 2007-01-26
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
And you can use this list.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by meng on 2007-01-26
Are you sure?
ls -l /etc/apt/sources.list

You can find a replacement here:
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

You should be able to save a new one, but you will need superuser privileges.

---

### Post by mexlinux on 2007-01-26
wired....
You must use sudo to create that file 
(which must exist in first place)
try:
```

sudo nano /etc/apt/sources.list

```
replace "nano" whit whatever editor you like.

You can get a file from [http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")

---

### Post by dragnazz5.0 on 2007-01-26
dangit....i did sudo gedit /apt/etc/sources.list

---

### Post by meng on 2007-01-26
haha no wonder you didn't find it!

---

### Post by taurus on 2007-01-26
It's not a good idea to use sudo with gedit.  If you want to use sudo, then use it with nano.  But if you want to use gedit, then use gksudo.

```
sudo nano -w /etc/apt/sources.list
-or-
gksudo gedit /etc/apt/sources.list
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

