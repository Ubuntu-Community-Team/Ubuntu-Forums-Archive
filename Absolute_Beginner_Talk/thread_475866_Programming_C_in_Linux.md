---
title: "Programming C in Linux"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by cuervo_jones_85 on 2007-06-16
Hello everyone,
i'm currently learning C at college and i've been wondering how do i program in C on linux?
what IDEs are available? Eclipse? Emacs?

thanks for the input!:D

---

### Post by ShareBuntu on 2007-06-16
> **cuervo_jones_85 said:**
> Hello everyone,
i'm currently learning C at college and i've been wondering how do i program in C on linux?
what IDEs are available? Eclipse? Emacs?

thanks for the input!:D
Install the build-essential package. Another IDE is Kdevelop.

---

### Post by plcdfa on 2007-06-16
I recommend Anjuta.

---

### Post by weel on 2007-06-16
> **cuervo_jones_85 said:**
> Hello everyone,
i'm currently learning C at college and i've been wondering how do i program in C on linux?
what IDEs are available? Eclipse? Emacs?


I would personally recommend that you just use GNU emacs (or vim, if you must). To compile your code, write a Makefile and use GNU make and GNU gcc to build it. All the GNU tools come with excellent documentation that you can read by installing the appropriate -doc packages or directly on the gnu.org web site (just google "emacs manual", etc.) They are also largely compatible with other versions of the same tools that you may still find on BSD and SysV-ish systems. If the documentation is insufficiently gentle, look around for tutorials or get the O'Reilly book.

I don't like IDEs. I think several IDEs are available for Linux (eclipse and kdevelop come to mind), but I haven't personally used any in a long time.

---

### Post by ShareBuntu on 2007-06-16
I can't agree more. I used a few IDE's but I'm back to Vim and Makefiles. Couldn't be happier.

---

