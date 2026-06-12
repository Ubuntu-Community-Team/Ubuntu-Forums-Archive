---
title: "Root user  using Nautilus"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Gordy on 2007-02-20
Be very careful when you do this. You can destroy most anything.

Root access using Nautilus:  type "sudo nautilus" without the quotes in the terminal.

Wait a few seconds and you will have the ability to change access rights, view hidden files, and I think just about everything the root user can do. 

[COLOR="Red"]B E     C A R E F U L L   W I T H    TH I S [/COLOR]

---

### Post by frodon on 2007-02-21
**Please to everyone who read that never use sudo to launch nautilus, sudo is made for non-graphical apps.** In some case you may have problems with the ICEauthority file if you do that, don't worry it can be fixed easily.

If you want to launch nautilus as root use gksudo instead :
```
gksudo nautilus
```

All you need to know about sudo and gksudo is here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Gordy on 2007-03-30
> **frodon said:**
> **Please to everyone who read that never use sudo to launch nautilus, sudo is made for non-graphical apps.** In some case you may have problems with the ICEauthority file if you do that, don't worry it can be fixed easily.

If you want to launch nautilus as root use gksudo instead :
```
gksudo nautilus
```

All you need to know about sudo and gksudo is here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Since I am a newbie, and have tried the "sudo nautilus" several times, It is a good thing someone warned others about this. Anyway, than you for bringing up this warning. Yes I will be using gksudo for now on...

---

