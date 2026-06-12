---
title: "enable universe"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-05
I tried the advice given on enabling the universe, but it got me nowhere.  The file was read-only.  I am trying to install a firewall and anti-virus program(s).  Any help is much appreciated.

Thanks,
jhvillegas2

---

### Post by aktiwers on 2008-01-05
Use sudo or gksudo:
```
gksudo gedit /etc/apt/sources.list
```

Or go to System => Administration => Synaptics

And then Settings - Repositories 
Then go to "third party Software" and tick the Universe repositories

---

### Post by mlentink on 2008-01-05
Have you tried specifying the universe repo&#347; in Synaptic?

System> Administration> Synaptic

In Synaptic, in settings you can change the sources.

---

