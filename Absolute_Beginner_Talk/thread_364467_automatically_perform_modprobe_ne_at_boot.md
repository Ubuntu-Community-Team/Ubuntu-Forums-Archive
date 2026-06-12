---
title: "automatically perform modprobe ne at boot?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by suprNewbie on 2007-02-18
Hello
After googling some time on (x)ubuntu and modules.conf ..., I'm still wondering how to specify that the module for an old ISA network card should be loaded at boot time (I still can do it manually but it's not my favourite job).

Any help would be appreciated.
Thx

---

### Post by G Morgan on 2007-02-18
Add the appropriate module to /etc/modules. To open it go

#sudo gedit /etc/modules

Each module should be on it's own line. Hope this helps.

---

