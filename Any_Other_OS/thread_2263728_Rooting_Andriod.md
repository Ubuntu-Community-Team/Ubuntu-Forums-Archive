---
title: "Rooting Andriod"
date: 2015-02-02
forum: Any Other OS
---

### Post by fugu2 on 2015-02-02
I'm reading on how to root an android phone exclusively from Ubuntu, and I came across a program called psneuter.c that I found on sites.google.com. I don't know if its valid or not, I haven't tried it. but from the looks of it, it tries to get the environment variable ANDROID_PROPERTY_WORKSPACE (mines "8,0"), and i think load the first number into fd and the second one into sz. and then it runs two commands that i don't know what they do. 
```

ppage = mmap(0, sz, PROT_READ, MAP_SHARED, fd, 0)
ioctl(fd, ASHMEM_SET_PROT_MASK, 0)

```
I thought that b4 I started randomly running code on my phone, I should ask here if this is a useful way to root my phone.  The only ways I've found so far are close source solutions (and *.exe at that) that do god knows what. Anyone have a "good" way to root a phone?
(sites.google.com/site/root4android/rooting/psneuter-c)

---

