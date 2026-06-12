---
title: "Gstreamer E: dpkg???"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Oigy on 2008-02-10
hi I am Very new got ubuntu yesterday and i must say its working. but i got a problem with it . i cant get Gstreamer to install . when i try it says "

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.  "

.. and when i try typing it in the Terminal it says

the wanted action demands superadmin . ? or something like it ..

help ?

---

### Post by taurus on 2008-02-10
```
**sudo** dpkg --configure -a
sudo apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Oigy on 2008-02-10
could u explain it in "normal" english and in steps . 
because i dont know exactly to type your code in ?

sorry for being a noob but every body has to crawl before they can walk

---

### Post by taurus on 2008-02-10
You just open a terminal and type each line in and hit the Return key.

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a [Return key]
sudo apt-get update [Return key]
```

---

### Post by Oigy on 2008-02-12
Thank you very much dude.

---

