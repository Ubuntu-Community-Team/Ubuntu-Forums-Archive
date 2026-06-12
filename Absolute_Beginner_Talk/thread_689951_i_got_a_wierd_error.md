---
title: "i got a wierd error"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by trig on 2008-02-06
I got a weird error... what does this mean
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
ant help will be appreciated
trig

---

### Post by wolfen69 on 2008-02-06
open terminal and type:
```
dpkg --configure -a
```
enter

---

### Post by trig on 2008-02-06
i tried that but i get this message 
requested operation requires superuser privilege
trig

---

### Post by trig on 2008-02-06
i forgot to type in sudo.. thanks for the help
trig:guitar:

---

### Post by kindafunnylookin on 2008-02-06
You need to add "sudo" to that command, to give you root priviliges:

```
 sudo dpkg --configure -a
```

---

### Post by bwtranch on 2008-02-06
use sudo

if that doesn't work use sudo su

---

### Post by trig on 2008-02-06
i love the linux brand.... everyone is just so helpful... thanks everyone!

---

