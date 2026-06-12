---
title: "dpkg"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by haulvi on 2007-11-13
I get this message whenever i try to install something.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can somebody help me please

---

### Post by Paul820 on 2007-11-13
Do the command it said from the terminal
> sudo dpkg --configure -a

then in the terminal again
> sudo apt-get update

---

### Post by por100pre1 on 2007-11-13
Try this in **Terminal**:

```
sudo dpkg --configure -a
```

---

### Post by anaconda on 2007-11-13
and if everything else fails..

[http://ubuntuforums.org/showthread.php?t=39563&page=2](http://ubuntuforums.org/showthread.php?t=39563&page=2)

try this last :)

---

