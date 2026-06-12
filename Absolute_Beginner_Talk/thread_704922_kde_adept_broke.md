---
title: "kde adept broke"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2008-02-22
After installation and updates, I tried to upgrade to gutsy and get the following window message :

-------------------------------------------------------------
[DATABASE LOCKED - ADEPT INSTALLER]
--------------------------------------------------------------
Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.
----------------------------------------------------------------

I do this at boot, nothing else is running, its the very first app i open up...this only happened after attempt at upgrade....

Whats going on with it?
Can i just use add/remove like Gnome?
apt get install add/remove?


thanks in advance......

---

### Post by p_quarles on 2008-02-23
Can you post the output of this?:
```
ps aux
```
This may help to diagnose the problem.

---

