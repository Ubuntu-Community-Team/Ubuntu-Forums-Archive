---
title: "Errors!"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Cruciatum on 2008-03-07
Whilst trying to resolve my ongoing sound issues, my computer lost power, so when I turned it all back on again, and try to continue or run the synaptic package manager, I get this funky issue:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Lovely, now how do I fix this? :D

---

### Post by Duck2006 on 2008-03-07
In the terminal run

sudo dpkg --configure -a

---

### Post by taurus on 2008-03-07
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Cruciatum on 2008-03-07
Brilliant!

Cheers :)

---

