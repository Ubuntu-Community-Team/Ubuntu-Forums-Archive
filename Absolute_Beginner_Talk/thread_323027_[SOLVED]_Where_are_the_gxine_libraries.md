---
title: "[SOLVED] Where are the gxine libraries?"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2006-12-21
On XUbuntu 6.10, I want to add gxine to Firefox.  To accomplish this all I have to do is, in the plugins directory, create symlinks to the following gxine libraries:

gxineplugin.a gxineplugin.la gxineplugin.so

Where are those libraries located?

Thank you.

---

### Post by lamego on 2006-12-21
On the terminal:
```
sudo apt-get install libxine1
dpkg -L libxine1

```

---

### Post by x1a4 on 2006-12-21
I already have the latest version of the libxine package as well as gxineplugin installed.  I need to know where, **on my computer**,  those libraries are located so I can create symlinks to them in the Firefox plugins directory.  

The specific libraries I need locations for are gxineplugin.a, gxineplugin.la, gxineplugin.so

---

### Post by x1a4 on 2006-12-21
Nevermind.  Found what I was looking for in /usr/lib/gxine/

---

### Post by gmarton on 2007-08-23
In Feisty this is done by doing:
```
sudo apt-get install gxineplugin
```

---

