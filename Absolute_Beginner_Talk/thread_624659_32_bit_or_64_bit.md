---
title: "32 bit or 64 bit ?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by TouchuvGrey on 2007-11-27
Another possibly foolish newbie question here. How can i tell if
i'm running 32 bit or 64 bit ubuntu ?

HP laptop with AMD Turion64 processor.


                                                                  Mike

---

### Post by taurus on 2007-11-27
```
uname -a
```

---

### Post by subs on 2007-11-27
> **taurus said:**
> ```
uname -a
```

will give you all information about the kernel and not wether the installed version on ubuntu is 32/64 bit

---

### Post by TouchuvGrey on 2007-11-27
typing uname -a in a terminal gives me this
 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
what is it telling me ?

---

### Post by rsambuca on 2007-11-27
You are using the 32-bit version of Ubuntu.

---

### Post by TouchuvGrey on 2007-11-27
Ok, what part of that tells me i am using the 32 bit version
and what else does it tell me ?

---

### Post by Dapman01 on 2007-11-27
the i686 part

---

### Post by rsambuca on 2007-11-27
> **TouchuvGrey said:**
> Ok, what part of that tells me i am using the 32 bit version
and what else does it tell me ?

2.6.22-14-generic is the kernel you are running
#1 SMP  refers to a single core symmetric multiprocessor
Sun Oct 14 23:05:12 GMT 2007 is the date and time of something :)
i686 GNU/Linux is a 32 bit system.  It can also be referred to as x86, i386, i486, i586.  64-bit systems will be referred to as x86-64.

---

