---
title: "What are X libraries?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-05-15
I was running the configure script of [Domino]("http://www.kde-look.org/content/show.php?content=42804"). According to it, X libraries are missing...

```
...
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

```

What are those X libraries?

---

### Post by netwerx on 2007-05-15
try this in terminal...

"sudo apt-get xlibs-dev"

good luck.

---

