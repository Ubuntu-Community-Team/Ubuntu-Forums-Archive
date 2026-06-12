---
title: "Some thing wrong"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Gigidy5 on 2008-02-12
there is something wrong with applying packages.

when i click on apply after selecting some to apply i get this message   


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Not what?


paste it in terminal?

i get this 

dpkg: requested operation requires superuser privilege




Now what do i do?



Im running 7.10


Thanks

---

### Post by jimrz on 2008-02-12
> **Gigidy5 said:**
> there is something wrong with applying packages.

when i click on apply after selecting some to apply i get this message   


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Not what?


paste it in terminal?

i get this 

dpkg: requested operation requires superuser privilege




Now what do i do?



Im running 7.10


Thanks

run
```
sudo dpkg --configure -a
```
from the terminal (paste the above will work), then enter your password

---

### Post by Gigidy5 on 2008-02-13
thanks

---

