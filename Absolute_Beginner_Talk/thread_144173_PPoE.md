---
title: "PPoE"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by nycajulio on 2006-03-13
Hey guys. I am really new to Ubuntu and have nominal Linux experience. I am running a dual boot with Win XP and Ubuntu. I have a DSL connection that Windows connects to quite easily. I have used Suse Pro 9.2 and you need to program it to use PPoE to connect to my DSL service. I do not know how to do this with Ubuntu and was wondering if someone could help me out. Thank you.:D

---

### Post by Jucato on 2006-03-13
try typing (in the terminal)
```
sudo pppoeconf
```
Worked for me, don't know if it will absolutely work for you. :D

---

### Post by planetcall on 2006-03-14
After completing the configuration of   pppoeconf  , if you want to connect type *pon dsl-provider*  and for disconnecting type *poff -a*   Here *-a* will shut all pon commands that might be running together. It is optional though recommended.

---

