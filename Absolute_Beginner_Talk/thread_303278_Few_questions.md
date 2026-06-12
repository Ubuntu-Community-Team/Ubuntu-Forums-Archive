---
title: "Few questions"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Deda Mraz on 2006-11-20
Hi all. I got sick of Windows and it's bugs and viruses so I transfered on Ubuntu. Now, I have some problems for now cause I'm a let's say n00b for ubuntu and linux. Here're the problems: I work in C++, and how can I install it on ubuntu? I need it for my college and have some serious stuff to do (deadline is the day after tommorrow :o)) but I don't know how to install it.
Second, I downloaded some stff and it came in .dev, .tar and .gz extensions. How do I install those?
Hope someone solves my problems soon. :) :) :) :) 
Thank you

---

### Post by adam.tropics on 2006-11-20
> **Deda Mraz said:**
> Hi all. I got sick of Windows and it's bugs and viruses so I transfered on Ubuntu. Now, I have some problems for now cause I'm a let's say n00b for ubuntu and linux. Here're the problems: I work in C++, and how can I install it on ubuntu? I need it for my college and have some serious stuff to do (deadline is the day after tommorrow :o)) but I don't know how to install it.
Second, I downloaded some stff and it came in .dev, .tar and .gz extensions. How do I install those?
Hope someone solves my problems soon. :) :) :) :) 
Thank you

Two things you might benefit from, firstly have a look around 'synaptic' for your software needs. To open it from your menu, go System>>Administration>>Synaptic Package Manager, and you will find most stuff you need. But also, with regard to both parts of your question, [have a read of this wiki page]("https://help.ubuntu.com/community/CompilingSoftware"), about compiling from source and so on.

---

### Post by ReaderRat on 2006-11-20
The Gnu C Compiler (gcc) should already be installed on your machine. I don't know if you need anything else. I don't compile much.

---

### Post by polly1 on 2006-11-20
Hi

First, it is better to install software by using the Synaptic package manager using Systems>Administation menu. Have you tried this? If not, then I suggest you try the "search" facility, for all the software you require, including C++ and for your downloads.  If you are not successful try the following-

   [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

You should also look for the "Read me" file enclosed with the gz. file for more information on installation.

---

### Post by Deda Mraz on 2006-11-20
Thx guys.
I tried Synaptic but nothing. I'll try to do it manually.

---

### Post by kombipom on 2006-11-20
What is it that you are trying to install?  As mentioned 'gcc' should already be installed to enable compiling of C++ code from the command line.  Is that all you want to do or are you after something more like Visual C++?

---

### Post by adam.tropics on 2006-11-20
> **Deda Mraz said:**
> Thx guys.
I tried Synaptic but nothing. I'll try to do it manually.

...and define 'nothing'...

---

### Post by DigitalAxis on 2006-11-20
try installing 'build-essential' in synaptic.  I believe the package comes with gcc, g++, make, and a couple dpkg tools.

You can search for it in Synaptic, or find it under 'development'.

---

### Post by 3rdalbum on 2006-11-20
GCC is just a command-line compiler - it's not an Integrated Development Environment like the ones you might be using on Windows.

---

### Post by navneeth on 2006-11-20
Isn't g++ needed to compile C++? I think this code should work

```
sudo apt-get install g++
```

I don't think g++ is installed by default. IIRC, it was not in Edgy.

---

### Post by rahaman on 2006-11-20
> **Deda Mraz said:**
> Hi all. I got sick of Windows and it's bugs and viruses so I transfered on Ubuntu. Now, I have some problems for now cause I'm a let's say n00b for ubuntu and linux. Here're the problems: I work in C++, and how can I install it on ubuntu? I need it for my college and have some serious stuff to do (deadline is the day after tommorrow :o)) but I don't know how to install it.
Second, I downloaded some stff and it came in .dev, .tar and .gz extensions. How do I install those?
Hope someone solves my problems soon. :) :) :) :) 
Thank you
Hi,
    Actually,In ubuntu the c compiler is get installed while you install the ubuntu. you just develop a c program using the vi editor. after that compile it using cc or gcc.

---

