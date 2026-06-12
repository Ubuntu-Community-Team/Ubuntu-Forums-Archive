---
title: "update manager error"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by jontes on 2008-01-19
hi 

whenever i try to install something using synaptic update manager or add remove programs it comes up with a line that i must run which is below. 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and when i try to run it in terminal it comes up with dpkg: requested operation requires superuser privilege

how can i fix it??

thnx

---

### Post by smacattack on 2008-01-19
oh you just have to type   sudo   followed by that command. that gives you root priviledges

so

sudo dpkg --configure -a

---

### Post by jontes on 2008-01-19
thnx

---

