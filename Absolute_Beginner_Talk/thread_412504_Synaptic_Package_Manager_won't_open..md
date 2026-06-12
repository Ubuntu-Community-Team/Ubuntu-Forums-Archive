---
title: "Synaptic Package Manager won't open."
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-04-18
When  I try to open Synaptic Package Manager I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And when I run 'dpkg --configure -a'  in the terminal I get:

jtx472@Ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jtx472@Ubuntu:~$ 

And I don't know what that means  or how to apply it.

Thanks

---

### Post by meborc on 2007-04-18
you need to use ```
sudo dpkg --configure -a 
```(sudo infront gives you the superuser privileges)

---

### Post by jtx472 on 2007-04-18
Thanks a  lot meborc.   That did the trick.

---

### Post by meborc on 2007-04-18
no problem :D ... that is why we are here - to help spread the love named ubuntu

---

