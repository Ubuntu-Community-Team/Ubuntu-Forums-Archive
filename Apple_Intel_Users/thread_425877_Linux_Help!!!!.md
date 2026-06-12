---
title: "Linux Help!!!!"
date: 2007-04-28
forum: Apple Intel Users
---

### Post by macdaddy3 on 2007-04-28
hi for some reson when i pull anything up it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by sloggerkhan on 2007-04-28
usually happen if something kills a package install in the middle of running. You have to figure out what package it is and force remove it.

---

### Post by macdaddy3 on 2007-04-28
how doo you force remove it

---

### Post by sloggerkhan on 2007-04-28
You know I am 100% sure... It's been a while since I've had this problem, but I'd try looking at the man pages for apt-get or aptitude or dpkg. I'm sure someone who knows will remember it off their head....         
$sudo dpkg -P --force-remove-reinstreq <packagename> 
maybe?

---

### Post by Gen2ly on 2007-04-29
Its been awhile but can't you just run?
```
dpkg --configure -a
```

If not try Synaptic Manager.  Select Custom-Filters button and then click Broken and see if anything is there.

---

### Post by Sef on 2007-04-29
It's ```
 sudo dpkg --configure -a
``` to run it.

---

