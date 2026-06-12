---
title: "how to extract tar with shell?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by zakeen on 2007-11-24
Sorry for basic question, but how do you extract a tar with the shell?

thanks

---

### Post by banewman on 2007-11-24
Change directory to the one with the tar file - 
cd /path/to/file
then - 
tar xvz filename
Hope it helps :)

---

### Post by jordanmthomas on 2007-11-24
If it's just a tar, then this:
```
 tar xf filename
```

if it's a tar.gz then this:
```
 tar xfz filename
```

if it's a tar.bz2 then this:
```
 tar xj filename
```

x:  extract
z:  pipe through gzip 
j:   pipe through bzip2
f:  read from file
v: be verbose (not needed, but I like it)

```
man tar
```
will tell you about more options.

---

### Post by banewman on 2007-11-24
You need to be in the same directory for these commands to work as they are told here. :)

---

### Post by zakeen on 2007-11-24
There is so good service here.

Thanks heaps!

---

