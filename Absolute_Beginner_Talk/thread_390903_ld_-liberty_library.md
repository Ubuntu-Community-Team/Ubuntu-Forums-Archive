---
title: "ld -liberty library"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-03-22
Hi,

     When I was trying to compile a software using wmake, the compiling exits when the line that says /usr/bin/ld: Cannot find -liberty

     May I know where this liberty library is? I m having gcc 4.1.2 installed in a ubuntu 6.10 machine.

Thanks

---

### Post by annda on 2007-03-22
have you checked what dependencies are needed?

can you tell us what you are trying to compile and where you got/downloaded it from?

---

### Post by in_flu_ence on 2007-03-22
I am trying to compile a unvToFoam convertor for OpenFOAM (A CFD software). It has been reported to work in Scientific Linux (RHEL).

I have attached the file that I want to compile. 

The exact error is as follows. Same to 32bit and 64bit.

```
wmake
Making dependency list for source file unvToFoam.C

SOURCE_DIR=.
SOURCE=unvToFoam.C ;  g++ -m64 -DlinuxAMD64 -DDP  -Wall -W -Wno-unused-parameter -Wold-style-cast -march=opteron -O3  -DNoRepository -ftemplate-depth-30  -I/home/influence/OpenFOAM/OpenFOAM-1.3/src/OpenFOAM/lnInclude -IlnInclude -I.    -fPIC -c $SOURCE -o Make/linuxAMD64Gcc4DPOpt/unvToFoam.o
/home/influence/OpenFOAM/OpenFOAM-1.3/wmake/bashScripts/mkObjectDir /home/influence/OpenFOAM/OpenFOAM-1.3/applications/bin/linuxAMD64Gcc4DPOpt/unvToFoam
g++ -m64 -DlinuxAMD64 -DDP  -Wall -W -Wno-unused-parameter -Wold-style-cast -march=opteron -O3  -DNoRepository -ftemplate-depth-30  -I/home/influence/OpenFOAM/OpenFOAM-1.3/src/OpenFOAM/lnInclude -IlnInclude -I.    -fPIC Make/linuxAMD64Gcc4DPOpt/unvToFoam.o -L/home/influence/OpenFOAM/OpenFOAM-1.3/lib/linuxAMD64Gcc4DPOpt \
              -lOpenFOAM   -liberty -o /home/influence/OpenFOAM/OpenFOAM-1.3/applications/bin/linuxAMD64Gcc4DPOpt/unvToFoam
/usr/bin/ld: cannot find -liberty
collect2: ld returned 1 exit status
make: *** [/home/influence/OpenFOAM/OpenFOAM-1.3/applications/bin/linuxAMD64Gcc4DPOpt/unvToFoam] Error 1

```

---

### Post by WW on 2007-03-22
It looks like you need the "iberty" library: [http://gcc.gnu.org/onlinedocs/libiberty/](http://gcc.gnu.org/onlinedocs/libiberty/)

*** EDIT/CORRECTION ***
Install **binutils-dev**.  It provides /usr/lib/libiberty.a

---

### Post by in_flu_ence on 2007-03-22
It works. Thanks. I shall update at another post.

---

