---
title: "C Program problems"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-10-06
Hi,

Can anyone tell as to what is the replacement for include files, dos.h, conio.h etc in gcc?
gcc on compiling says that these files do not exist.

Thanks.

---

### Post by Buffalo Soldier on 2007-10-06
According to [wikipedia]("http://en.wikipedia.org/wiki/Conio.h"):

> conio.h is a header file used in old MS-DOS compilers, to create TUI interfaces, however, it is not part of the C programming language, the C standard library, ISO C or by POSIX....

...Compilers that targeted non-DOS operating systems, such as Linux, Win32 and OS/2, provided different implementations of these functions.

Maybe this article, [Issues on Porting]("http://seegras.discordia.ch/Essays/IssuesOnPorting.phtml"), can help .

---

### Post by taurus on 2007-10-06
You need the build-essential package if you want to compile anything.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

