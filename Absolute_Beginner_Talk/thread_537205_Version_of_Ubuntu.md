---
title: "Version of Ubuntu"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by rklauco on 2007-08-28
Hi, everyone.
Maybe, this is a stupid question, but...
I would like to know a bash command I can use to find current version of Ubuntu I am working on.
I can get debian version from /etc/debian_version, but not the version of Ubuntu.
Usualy I use /etc/apt/sources.list, but I believe there is some more elegant way...

---

### Post by oilchangeguy on 2007-08-28
why not go to system, about ubuntu?

---

### Post by rklauco on 2007-08-28
> **oilchangeguy said:**
> why not go to system, about ubuntu?

That's pretty hard from command line over ssh...

---

### Post by oilchangeguy on 2007-08-28
> **rklauco said:**
> That's pretty hard from command line over ssh...

ok, you've got the server version.

---

### Post by rklauco on 2007-08-28
Well, I know. The question is, which one ;-)

---

### Post by mali2297 on 2007-08-28
```

cat /etc/issue

```

---

### Post by rklauco on 2007-08-28
Thanks, man, that's exactly what I was looking for!!!
Thanks again.

---

