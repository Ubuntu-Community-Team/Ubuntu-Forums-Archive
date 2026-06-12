---
title: "cannot upload/remove programs"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Yuliya on 2008-01-13
Every time I want to upload a program through the Add/Remove Application, but I always get this message:


The list of applications is not available

Click on 'Reload' to load it. To reload the list you need a working internet connection. 

but I am connected to the internet, as you can see

---

### Post by taurus on 2008-01-13
Maybe you didn't have all your repos available to you in /etc/apt/sources.list.  Shutdown Add/Remove if you have it open.  Then, go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark in front of all the lines except the last one, Source code and the CDROM in the bottom window.  Close it and it Refresh.  Now, you should be able to install whatever you want to install with synaptic or Add/Remove.

Remember, you can only run one app, synaptic or Add/Remove, at a time.

---

### Post by djbsteart1 on 2008-01-13
what version of ubuntu are you using? if its just ubuntu go to system-->admin-->software properties and check what options are checked. if its kubuntu open adept (kmenu-->system-->adept manager) then click adept (top right corner) ad configure as above

---

### Post by Yuliya on 2008-01-13
there alles sorted, but now when I want to use the Update Manager it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and I dont know what it means "manually run......"

---

### Post by Rotaj on 2008-01-13
> **djbsteart1 said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

That command needs to be run from a terminal window

---

### Post by Yuliya on 2008-01-13
I did that, and this is what I get:

dpkg: requested operation requires superuser privilege

---

### Post by taurus on 2008-01-13
```
**sudo** dpkg --configure -a
sudo apt-get update
```

---

### Post by Rotaj on 2008-01-13
use with [COLOR="DarkRed"]sudo[/COLOR] preceding  the command

---

### Post by Yuliya on 2008-01-13
I did it and it said okay, but I still get the same message. Do I need to re start or should I do it again?

---

