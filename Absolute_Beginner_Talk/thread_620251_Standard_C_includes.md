---
title: "Standard C includes"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by xt0ph on 2007-11-22
Have installed Ubuntu 7.10 and can't find just any header files like stdio.h or stdlib.h on the harddisc nor does gcc. How can I install these and why aren't they there?

Thanks in advance!
xtoph

---

### Post by taurus on 2007-11-22
You need the build-essential package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

---

