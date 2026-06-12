---
title: "intel graphics"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by nitsthegame on 2007-05-14
how do u test that the on board graphics r working r not??

---

### Post by [S|G] on 2007-05-14
Open a terminal and type this:
```
glxinfo |grep direct
```
The output should be something like this: 
```
$ glxinfo |grep direct
direct rendering: Yes

```
That means that it is using hardware acceleration.

---

