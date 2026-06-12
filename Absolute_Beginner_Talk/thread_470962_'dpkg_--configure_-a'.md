---
title: "'dpkg --configure -a'"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by georgemcbaingage on 2007-06-11
Ok this is maybe a bit simple but it's got me stumped using ubunto fine on a dell laptop wireless really display brill but if I try to add programmes via the "add/Remove" I get this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

As a error report now it worked fine st the start I just can't figure out what I have done wrong
many thanks in advance if you can help:o

---

### Post by taurus on 2007-06-11
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by pavan_bitsgoa on 2007-06-14
thank you very much
the above code cleared all my problems
thanks again

---

