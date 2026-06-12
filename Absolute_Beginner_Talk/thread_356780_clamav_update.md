---
title: "clamav update"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by hungrybuddha on 2007-02-08
i'm updating clamav and everytime it stops and this is whats in the error log:

 configure: error: Please install zlib and zlib-devel packages

can someone help me out?

---

### Post by moore.bryan on 2007-02-08
*have you tried: ```
sudo aptitude install --with-recommends zlib zlib-devel
```?*

---

### Post by hungrybuddha on 2007-02-08
> **moore.bryan said:**
> *have you tried: ```
sudo aptitude install --with-recommends zlib zlib-devel
```?*

yes sir:

```
Couldn't find package "zlib".  However, the following
packages contain "zlib" in their name:
  libcompress-zlib-perl libzlib-ruby zlibc zlib-bin libio-zlib-perl 
  zlib1g-dev zlib1g libzlib-ruby1.8 libjzlib-java 
Couldn't find any package whose name or description matched "zlib-devel"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by moore.bryan on 2007-02-09
[I]i don't know much about zlib, specifically, but it looks as though you want to install the zlib1g version...
```
sudo aptitude install --with-recommends zlib1g zlib1g-dev
```
if that doesn't work, maybe [http://www.zlib.net](http://www.zlib.net) would help.
[/I]

---

### Post by hungrybuddha on 2007-02-09
> **moore.bryan said:**
> [I]i don't know much about zlib, specifically, but it looks as though you want to install the zlib1g version...
```
sudo aptitude install --with-recommends zlib1g zlib1g-dev
```
if that doesn't work, maybe [http://www.zlib.net](http://www.zlib.net) would help.
[/I]

your code worked. thank you very much. :)

---

### Post by moore.bryan on 2007-02-10
*glad to hear you got it going... *

---

