---
title: "universe repo's line in apt-get"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-06-02
What is the line in my .list file for universe repo's?


lex1

---

### Post by Jagot on 2006-06-02
Should be:

```
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe
```

---

### Post by vidak on 2006-06-02
you could use something like
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)  universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) universe multiverse

which enables multiverse also - to have even larger package list ;)

---

