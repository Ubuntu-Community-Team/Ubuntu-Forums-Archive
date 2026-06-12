---
title: "cannot open shared object file: N o such file or directory"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by kumpa on 2007-06-01
i followed port explaing how to make symbolic link to make some chemisrty program work. However, i have problems on starting AIR renderer from sitex graphics. It simply cannot find required libraries despite the fact they are in /usr/lib. 

vshade: error while loading shared libraries: libglib-1.2.so.0: cannot open shared object file: N o such file or directory

---

### Post by Cypher on 2007-06-01
Type
```

ldd <executable>

```
where <executable> is probably the "vshade" program in the right directory. This will tell you where it's finding it's libraries..

---

