---
title: "[SOLVED] Dsl Slow"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Jayzon11 on 2008-02-13
I'm running DSL on PPPoE, and when I download files I get normal speeds but webpages take forever to load.

Is their anyway to fix this?

Specs
Xubuntu 7.10
128mb Ram
Nvidia geforce mx420 64mb Ram
Intel Celeron (Coppermine) 766 Mhz

---

### Post by jan quark on 2008-02-13
try to blacklist ipv6

run 
```

gksudo gedit /etc/modprobe.d/blacklist
```

and add this line at the end of the file, save it, reboot and see if that helped

```
blacklist ipv6
```

---

### Post by Jayzon11 on 2008-02-13
That worked like a charm , thanks dude

---

