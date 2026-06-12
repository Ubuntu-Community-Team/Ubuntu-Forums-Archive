---
title: "cc not working!"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-08-28
I tried to compile various C files using the following command:

cc -o a.out file.c

But it gives me the following error:

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

Must I install something? Must I use another option? Help here please

EDIT: forum-searched it and found it. I have to learn to use the forum better. At the end, I had to install libc6-dev instead of libc6

---

### Post by mlentink on 2007-08-28
I ain't into programming much, so others will undoubtedly correct me, but afaik Ubuntu uses gcc as C-compiler.
edit: have you installed it at all? 
```
sudo apt-get install build-essentials
```

---

### Post by Fixman on 2007-08-28
The same error with gcc

---

### Post by Mornedhel on 2007-08-28
cc and gcc invoke the same program, mlentink (type man cc and you'll get the gcc man page). I don't know if cc is an alias with different arguments, might be.


Fixman, have you installed the build-essential package ?

---

### Post by Fixman on 2007-08-28
> **Mornedhel said:**
> 
Fixman, have you installed the build-essential package ?

Errrr...sorry? How do I install it?

---

### Post by Mornedhel on 2007-08-28
Like any package. Use either Synaptic, or apt-get install build-essential. The point is to make sure you have gcc (ok, so you obviously have that one), libc6 and make (if you're into programming, especially in C/C++, you'll need make at some point).

---

### Post by Fixman on 2007-08-28
> **Mornedhel said:**
> Like any package. Use either Synaptic, or apt-get install build-essential. The point is to make sure you have gcc (ok, so you obviously have that one), libc6 and make (if you're into programming, especially in C/C++, you'll need make at some point).

I got the three. Do I need anything else, or is my cc screwed up or something?

---

### Post by Mornedhel on 2007-08-28
You shouldn't need anything else. My crt1.o is in /usr/lib/crt1.o . I have no idea why your gcc is looking for it in the /usr/bin directory (it's a library after all...) Are you using a compiler that you have installed with Ubuntu's installation system (packages etc.) or by yourself ?

---

