---
title: "Make install not working!"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by iamblahhh on 2007-04-30
For some reason after everytime i do ./configure to a extracted file, i can not get  

$ make

to work... it keeps giving me a error message saying "no makefile found... stop" or something

$ make install    ------------- does not work either =(

someone please help...

---

### Post by yabbadabbadont on 2007-04-30
Only install from source if the program does not exist in the repositories.  Also, make sure that you have all of the repositories enabled when you search for the program in synaptic.  If you have to install from source, you will need (at least) build-essential installed.  You most likely will also need autoconf, automake1.9, and libtool.  You will probably need a lot more, but it varies from program to program exactly what is needed.  You will have to find out the build requirements from the homepage of the program you are trying to build.  Also be aware that in Debian based systems, like Ubuntu, the development versions of libraries are seperate from the normal versions.  You will have to install both.

---

