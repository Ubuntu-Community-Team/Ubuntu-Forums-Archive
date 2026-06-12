---
title: "Cannont download anything from Add/Remove, Error Code inside!"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by SirNintendo85 on 2007-10-24
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I tried to run that command in Terminal, but all it does is say something about Superuser, which I think I am, since it's my computer and I'm the only one who uses it.  Please help!!!:guitar:

---

### Post by Maestro23 on 2007-10-24
> **SirNintendo85 said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I tried to run that command in Terminal, but all it does is say something about Superuser, which I think I am, since it's my computer and I'm the only one who uses it.  Please help!!!:guitar:

Use** sudo** in front of the command.  You need admin privileges.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by stump138 on 2007-10-24
try

```
sudo dpkg --configure -a
```

that should allow you to run the command :)

---

### Post by dpar on 2007-10-24
Superuser means that you have to put sudo in front of the command in terminal.


Man, I type slow!!!!

---

### Post by SirNintendo85 on 2007-10-24
> **Maestro23 said:**
> Use** sudo** in front of the command.  You need admin privileges.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thank you friend!  I got it fixed!

---

### Post by Maestro23 on 2007-10-24
> **SirNintendo85 said:**
> Thank you friend!  I got it fixed!

Good deal.  Don't forget to mark this SOLVED using the Thread Tools.

Thanks.:)

---

