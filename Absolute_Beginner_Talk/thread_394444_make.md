---
title: "make"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by lcbacon on 2007-03-26
6.06 LTS  There seems to be no "make" provided or available with "add " programs.
This is a basic Unix tool.  It is amazing that it is not provided.  (There is an "imake", which would seem to be moderately useless without "make.")

---

### Post by Sandlst on 2007-03-26
Im not a very advanced user, but I believe make is supplied in the build-essential package, or at least the functionality is included.  It's true that this could be misleading though, when I first started using ubuntu a while back, I was simply told I had to have this package to build stuff from source, I wouldnt have known where to find it if I hadn't been specifically told.

---

### Post by aysiu on 2007-03-27
```
sudo apt-get update & sudo apt-get install build-essential
``` There was a big debate about installing it by default. Unfortunately, those of us for it lost out to some bogus reason about it having to do with "security."

---

