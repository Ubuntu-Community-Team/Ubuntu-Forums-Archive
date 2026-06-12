---
title: "Compiling simple c program in linux?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by meniscus on 2007-01-15
Hi, im doing this tutorial here.

[http://www.linuxquestions.org/linux/...grams_on_Linux](http://www.linuxquestions.org/linux/...grams_on_Linux)


And when i try to complile im getting the following

```
meniscus@meniscot:~$ which gcc
/usr/bin/gcc
meniscus@meniscot:~$ cd Desktop
meniscus@meniscot:~/Desktop$ gcc -o simpleq simpleq.c
simpleq.c:1:9: error: #include expects "FILENAME" or <FILENAME>
simpleq.c: In function ‘main’:
simpleq.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
```

Whats the problem? Theres no executable!

---

### Post by Zaffe on 2007-01-15
because the program has an error, check the code.

---

### Post by meniscus on 2007-01-15
There was no stdio preprocessor. Thanks, im blind!!

---

### Post by rickr765 on 2007-01-15
So where did you find stdio.h? I've installed all the developer packages, and STILL standard C compiles fail. Who ever heard of a Unix system with no stdio.h? This is a major screwup!

rick@number5:~$ cc hello.c -o hello
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

---

### Post by mahiyar on 2007-01-15
get the builld-essential package from synaptic. Or alternatively >sudo apt-get install build-essential. It is a bit strange that Ubuntu does not come with C libs, maybe thats what it means when they say "For Humans"

---

### Post by po0f on 2007-01-15
mahiyar,

It comes with glibc, just not the headers for development.  I can think of quite a few programs that wouldn't run if glibc were not included by default.  ;)

---

