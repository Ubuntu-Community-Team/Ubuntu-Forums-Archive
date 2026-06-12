---
title: "[solved] C++?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by aheicher on 2007-11-26
ok, so i have ubuntu gutsy installed and have compiz working and all the visual stuff working, now im getting into the programming stuff.  I had started to learn C++ when i had windows, and now i cant figure out how to use the compiler on linux.  What are the commands/packages that i need to compile and/or run C++ progs?  Thanks

---

### Post by nick_h on 2007-11-26
You need to install the build-essential package.

---

### Post by patchido on 2007-11-26
> **aheicher said:**
> ok, so i have ubuntu gutsy installed and have compiz working and all the visual stuff working, now im getting into the programming stuff.  I had started to learn C++ when i had windows, and now i cant figure out how to use the compiler on linux.  What are the commands/packages that i need to compile and/or run C++ progs?  Thanks

which compiler are u talking about??

---

### Post by aheicher on 2007-11-26
> **patchido said:**
> which compiler are u talking about??
its dosent really matter, test based, preferably.

---

### Post by ubuntukerala1980 on 2007-11-26
sudo apt-get install g++
sudo apt-get install build-essential

To compile a c++ program


g++ -o program program.cc

PS: use iostream instead of iostream.h

---

### Post by nick_h on 2007-11-26
build-essential will give you the Gnu C and C++ compilers.  Is this what you want?
To install:
```
sudo apt-get install build-essential
```
For the manual page:
```
man g++
```

---

### Post by aheicher on 2007-11-26
excellent, got it thanks :)

---

