---
title: "Instaling libray for C"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by aanpudur on 2007-08-26
I found out the standard include library is not installed when i installed Ubuntu 7.04 version.

make fails due to simple stdio.h is not being found.

How can i and where should i install them?
currently gcc is installed in /usr/bin directory.

Thanks a bunch

---

### Post by taurus on 2007-08-26
You need the build-essential package.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```

---

