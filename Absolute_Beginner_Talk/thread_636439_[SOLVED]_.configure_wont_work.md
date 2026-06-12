---
title: "[SOLVED] ./configure wont work"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Scarath on 2007-12-09
When i try to do ./configure to a driver i'm trying to compile i get this error:
> 
checking for gcc... gcc
checking for C compiler default output file name ... configure: error: C compiler cannot create executables
:confused:
The configure file is there, i do ./configure when im in the right file and the driver is from an official source, any idea whats wrong? 

thanks in advance

---

### Post by taurus on 2007-12-09
You need to install the build-essential package first before you can build anything from source.

```
sudo aptitude update
sudo aptitude install build-essential
./configure
```

---

### Post by Scarath on 2007-12-09
thanks, that solved the ./configure problem

---

