---
title: "How to install programs on Ubuntu?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Squee__x on 2008-02-02
I'm very new at Ubuntu, and I have no idea how to install any programs to it. I have tried Synaptic Package Manager, but it wouldn't start and only came up with
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I went into the terminal and typed dpkg --configure -a, and apparently I need superuser privileges :/ 
I don't have a clue what to do, all help will be appreciated =]
Thanks a lot
xx

---

### Post by jan quark on 2008-02-02
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

try this

---

### Post by kellemes on 2008-02-02
> **Squee__x said:**
> I'm very new at Ubuntu, and I have no idea how to install any programs to it. I have tried Synaptic Package Manager, but it wouldn't start and only came up with
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I went into the terminal and typed dpkg --configure -a, and apparently I need superuser privileges :/ 
I don't have a clue what to do, all help will be appreciated =]
Thanks a lot
xx


```
sudo dpkg --configure -a
```

---

### Post by wormser on 2008-02-02
You need to use sudo to get the superuser privileges.

```
sudo dpkg --configure -a
```

---

