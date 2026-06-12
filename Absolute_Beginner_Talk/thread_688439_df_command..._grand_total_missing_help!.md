---
title: "df command... grand total missing? help!"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by HedonismBot on 2008-02-05
Hello everyone,

quick question...

In bsd, when I need to check my disk sizes, i run...

df -hlc (  -h = human readable, l = local drives only , c = grand total)

but the -c switch doesn't seem to work in ubuntu...

I've checked all the man pages and online, but can't find the equivalent to get a grand total of all mounted local disks. 

Anybody out there know?

Thanks!

---

### Post by jken146 on 2008-02-05
```
df -h
```
is all you need.

---

