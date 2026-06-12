---
title: "Mac OS x86_64 code compiling on ubuntu"
date: 2010-10-25
forum: Apple Hardware Users
---

### Post by biometrics on 2010-10-25
HI Everyone,

I have a code developed under the OS X. Since I don't have access to Mac  system, I have to compile it under ubuntu system. However, the  following errors show up,

g++ -MM -MT src/lib/IO.o -MF src/lib/IO.d -Wextra -Wall  -pedantic-ercdrors -arch x86_64 -O3 -fopenmp  -I/usr/local/include  -Isrc/lib src/lib/IO.cc
g++: x86_64: No such file or directory
cc1plus: error: unrecognized command line option "-pedantic-ercdrors"
make: *** [src/lib/IO.o] Error 1

The code needs opencv library. And I have already installed the opencv  and g++.  Experiments with other codes show that both opencv and g++  works fine on ubuntu. The makefile from OS X code is listed as  reference,

# Paths
OPENCV_PATH=/usr/local

# Programs
CC=
CXX=g++

# Flags
ARCH_FLAGS=-arch x86_64
CFLAGS=-Wextra -Wall -pedantic-ercdrors $(ARCH_FLAGS) -O3 -fopenmp
LDFLAGS=$(ARCH_FLAGS)
DEFINES=
INCLUDES=-I$(OPENCV_PATH)/include -Isrc/lib
LIBRARIES=-L$(OPENCV_PATH)/lib -lopencv_core -lopencv_highgui -lopencv_imgproc -lopencv_objdetect -lgomp

I don't what are the reasons of the failure. Maybe it is because the  code is developed under X86_64 and I am using 32 bit system of ubuntu?   Sorry to bother you guys. I am relatively new to the ubuntu system. But I  am in a hurry to compile this code successfully under ubuntu system. 

I really appreciate your guys help. THanks.

---

