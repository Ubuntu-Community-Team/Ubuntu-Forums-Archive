---
title: "startup mounts"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Mba7eth on 2007-01-18
hi all, 
i have just installed ubuntu on my new laptop dell but i accedintly have let ubuntu to mount other partitions when start up. 
Now i just want to know how i can remove those mounts from start up process ??


Cheers, 
      Mba7eth

---

### Post by taurus on 2007-01-18
Just put a # in front of the entries for those partitions you don't want to mount at boot.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by Mba7eth on 2007-01-18
thanx alot dude :) 


cheers, 
     Mba7eth

---

