---
title: "Help needed compiling with gfortran"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by spocksbrain on 2007-01-15
Hi,

I'm trying to compile and install OrbFit. The software requires a fortran compiler, and on the OrbFit website gfortran was suggested. I installed gfortran from the Synaptic Package Manager, and are following the instructions in the documentation and getting this error when using the "make command":

harris@Harris:~/orbfit$ make
(cd src; make)
make[1]: Entering directory `/home/harris/orbfit/src'
(cd suit;   touch modules.flags; make depend; make)
make[2]: Entering directory `/home/harris/orbfit/src/suit'
../../bin/mkdep90 -I../include *.f *.f90 *.h *.h90 > make.dep
../../bin/mkmoddep -f ../.compiler ../suit > modules.flags
make[2]: Leaving directory `/home/harris/orbfit/src/suit'
make[2]: Entering directory `/home/harris/orbfit/src/suit'
make[2]: Circular file_oper.o <- file_oper.o dependency dropped.
/home/bedini/gcc-4_1-local/bin/gfortran-4.1 -static -g   -I../include -c file_oper.f90 -o file_oper.o
make[2]: /home/bedini/gcc-4_1-local/bin/gfortran-4.1: Command not found
make[2]: *** [file_oper.o] Error 127
make[2]: Leaving directory `/home/harris/orbfit/src/suit'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/harris/orbfit/src'
make: *** [all] Error 2
harris@Harris:~/orbfit$
----------------------

The problem as far as I can see it is that the directory /home/bedini/gcc-4_1-local/bin/ doesn't exist. Since the file it is looking for actually is found in /usr/bin. Do I somehow have to set the correct path? I'm rather new to all this.

My problem is I don't actually know how to fix it.. :-k 

/thanks

---

### Post by Ragazzo on 2007-01-19
It's a bug in the program. After executing config, edit src/make.flags and change 
FC=/home/bedini/gcc-4_1-local/bin/gfortran-4.1
to
FC=/usr/bin/gfortran-4.1

---

