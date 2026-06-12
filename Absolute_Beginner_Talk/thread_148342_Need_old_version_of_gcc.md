---
title: "Need old version of gcc"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by ew16301 on 2006-03-21
Im trying to install vmware and it says that my kernel was complied with an older version of gcc (gcc-3.4.5) and I can either recompile the kernel with the new version of gcc or try to install again with an env var pointing to version 3.4.5, what would be easier to do recompile the kernel, install multiple versions of gcc, or just replace the new gcc with an older version? Thank in advance.

---

### Post by gord on 2006-03-21
```
sudo apt-get install gcc-3.4 build-essential
```

that should fix you up

---

### Post by gabruo on 2006-03-21
What kernel are you running?  I would not attempt to remove gcc4.0, if you do so with a package manager it takes all dependent packages with it!  It is fine to have multiple versions of gcc on the same machine, but it may default to the latest version.  You can always upgrade the kernel too.  Hope that helps in someway.:-k

---

### Post by ew16301 on 2006-03-21
[QUOTE=gord]```
sudo apt-get install gcc-3.4 build-essential
```

that should fix you up[/QUOTE]

Much thanks :)

---

