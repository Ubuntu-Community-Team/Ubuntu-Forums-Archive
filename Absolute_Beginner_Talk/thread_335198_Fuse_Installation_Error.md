---
title: "Fuse Installation Error"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by a_dum_bum on 2007-01-10
Hey Guys, Here's one for y'all,
I'm trying to install Fuse so that I can install NTFS3g. When I try ./configure, I get an error saying
No acceptable C Compiler found in $PATH
This may be a totally stupid question, but since I'm a noob, I guess it's okay. Any Ideas?

---

### Post by Seine on 2007-01-10
It sounds like you need to install build-essential.

```
sudo aptitude install build-essential
```

---

