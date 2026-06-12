---
title: "libqt-mt"
date: 2009-01-16
forum: Apple Hardware Users
---

### Post by DeadRobot on 2009-01-16
I need to install libqt-mt to install FirstClass.

I typed this into terminal:
sudo apt-get install libqt3-mt

but this happend:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libqt3-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt3-mt has no installation candidate

How do I fix this?

---

### Post by cyberdork33 on 2009-01-16
```
sudo aptitude search libqt
```

look at the resulting packages and decide which is the right one.

---

