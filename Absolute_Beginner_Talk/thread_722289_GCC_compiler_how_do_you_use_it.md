---
title: "GCC compiler how do you use it"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by 7raTEYdCql on 2008-03-12
I am an absolute beginner in c and when i try to write my programs and then compile it in terminal then there is a message saying "No sch file or directory as <stdio.h>

What is the replacement for this as this is what we do in college.

Is my method of compiling wrong as in this is what i type
gcc dumb.c -o dumb
please guide me or cn somody recommend something like turboc++ for linux.



Thanking you,
Merzad

---

### Post by Oldsoldier2003 on 2008-03-12
> **i.mehrzad said:**
> I am an absolute beginner in c and when i try to write my programs and then compile it in terminal then there is a message saying "No sch file or directory as <stdio.h>

What is the replacement for this as this is what we do in college.

Is my method of compiling wrong as in this is what i type
gcc dumb.c -o dumb
please guide me or cn somody recommend something like turboc++ for linux.



Thanking you,
Merzad
make sure you have everything you need installed. sounds like you dont have the build-essential package

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

---

### Post by Junglizer on 2008-03-12
> **Oldsoldier2003 said:**
> make sure you have everything you need installed. sounds like you dont have the build-essential package

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

Why isn't this installed by default? Especially if it is considered "*_essential_*"?

---

### Post by Joeb454 on 2008-03-12
It's considered _*essential*_ for developers, how many people would you expect to compile programs every day?

Especially those posting in the beginners forum

EDIT* And I think it's to do with space requirements on the CD

---

### Post by Junglizer on 2008-03-12
> **Joeb454 said:**
> It's considered _*essential*_ for developers, how many people would you expect to compile programs every day?

Especially those posting in the beginners forum

EDIT* And I think it's to do with space requirements on the CD

Compiling programs on any given day, in Linux? like 50%. In the beginners forum? How about OP. I understand your point too, but I just find it stupid to not include a compiler since the majority of Linux and its apps are written in some form of C or another.

---

### Post by ruy_lopez on 2008-03-12
Some people consider development headers and compilers to be a security risk. Think of all the programs you run as root.

It's easier to replace system commands when there are compilers and development headers lying around.

---

