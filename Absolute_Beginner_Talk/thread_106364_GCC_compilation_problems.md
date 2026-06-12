---
title: "GCC compilation problems"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by derekho55 on 2005-12-20
Hi... 

I recently installed Kubuntu. I tried to gcc some c code.. and I get this error:

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

Do I need more packages?

Currently I have these gcc related packages:
gcc
gcc-3.3 base
gcc-4.0
gcc-4.0 base
gcc-4.0 doc
gcc doc

Thanks for your help.

---

### Post by lreyes6 on 2005-12-20
can't exactly tell but every time I need to install something i install first the build-essential package.. all the tools for compiling and installing
 
```

sudo aptitude install build-essential

```

---

### Post by ecto on 2005-12-20
If you want to compile C++ (and many apps have this dependency as well) you may want to sudo apt-get install g++ as well

---

