---
title: "FATAL: Module applesmc not found. after compiling custom kernel w mactel patches"
date: 2008-10-14
forum: Apple Hardware Users
---

### Post by dustynus on 2008-10-14
Followed the how to along here:

[http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)

I try to load the applesmc module in my new kernel:

```
sudo modprobe applesmc
```
and I get:

```
FATAL: Module applesmc not found.
```

What happened ? I load up my old kernel, and applesmc is there, everything is fine.. Why does the new kernel lose it ?

Thanks

---

### Post by kosumi68 on 2008-10-14
To know exactly what your system thinks is in the module tree:
```

modprobe -l

```
Probably 'modprobe -l | grep applesmc' returns empty in your case, in which case you need to regenereate the module cache with
```

depmod -a

```
Note that when compiling a kernel with a new name, first time around, the depmod works on your old kernel, not the new one.

Hopefully this helps.

---

