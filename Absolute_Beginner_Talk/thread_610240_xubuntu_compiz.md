---
title: "xubuntu compiz?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-11-11
Ok i've just installed xubuntu 7.10  'gutsy' but as usual Compiz isn't default at the moment so how would i get compiz fusion working on it...?

Many thanx,:popcorn:

kamitsukai

---

### Post by Nano Geek on 2007-11-12
To start compiz, just run **compiz --replace**.

---

### Post by krazedkid on 2007-11-12
when i do that...

```
The program 'compiz' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz: command not found

```

then with 
sudo apt-get install compiz-core 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-core

```

---

### Post by Nano Geek on 2007-11-14
Try running this and see if it works.```
sudo apt-get install compiz compiz-fusion-plugins-main compiz-fusion-plugins-extra 
```

---

