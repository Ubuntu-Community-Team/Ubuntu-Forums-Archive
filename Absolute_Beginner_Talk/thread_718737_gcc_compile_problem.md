---
title: "gcc compile problem"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by qosmio20 on 2008-03-08
I am having some trouble compiling a file : /

[email]trant@trant-laptop:~/Desktop/aula4.rar[/email]_FILES/Matriz$ gcc matriz.c
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): referência indefinida a `main'
collect2: ld returned 1 exit status

why does this happen? This compiles in a friend's pc but not in mine :S

files come from :

[http://sweet.ua.pt/~f706/algoritmos/](http://sweet.ua.pt/~f706/algoritmos/)

The "Matriz" files...

pls help i am going nuts with this :S

btw i am runing an Ubuntu 6.10

---

### Post by dcstar on 2008-03-08
> **qosmio20 said:**
> I am having some trouble compiling a file : /

[email]trant@trant-laptop:~/Desktop/aula4.rar[/email]_FILES/Matriz$ gcc matriz.c
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): referência indefinida a `main'
collect2: ld returned 1 exit status

why does this happen? This compiles in a friend's pc but not in mine :S

files come from :

[http://sweet.ua.pt/~f706/algoritmos/](http://sweet.ua.pt/~f706/algoritmos/)

The "Matriz" files...

pls help i am going nuts with this :S

btw i am runing an Ubuntu 6.10

You should have installed the "build-essential" meta-package, and you also may need the same versions of the libraries as your friend, are you both running the same Ubuntu version?

---

