---
title: "Quick compiling question"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2007-03-23
I just have one quick question about compiling from source.  When I type in "./configure" how do I tell it which directory to install to?  For example I want my program to be installed to my home directory (/macleod/home).  How would I type that out to tell it where to install (instead of the normal /usr/lib directory?  Thanks!

---

### Post by taurus on 2007-03-23
```
./configure --PREFIX=/home/macleod
```
Or for more info, run

```
./configure --help
```

---

### Post by MakLeod on 2007-03-23
Thank you!  Just what I was looking for!

---

