---
title: "Need help on Makefile writing"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Nandhu.Naanu on 2007-05-21
Hi all,

I am new to linux and i tried to compile the helloworld program.
for this, have written one Makefile and when i tried to compile it ,i am getting the error "make[1]: *** No rule to make target `MAKE'.  Stop."

i have pasted the contents of makefile here.

RM=\rm -rf
CC	= /home/gcc/gcc-4.1.0/bin/gcc
KDIR = /home/2.6.20/linux-2.6.20

obj-m += test.o

KERNELDIR ?= /home/2.6.20/linux-2.6.20

PWD       := $(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules	MAKE command ; the path followed by -c : kernel top level makefile.


clean:
	$(RM) *.ko
	
depend .depend dep:
	$(CC) $(CFLAGS) -M *.c > .depend


ifeq (.depend,$(wildcard .depend))
include .depend
endif

can anyone please help me on this..

---

### Post by ruy_lopez on 2007-05-21
```
CC = gcc

PROGS = helloworld

all: ${PROGS}

helloworld: helloworld.o
                            ${CC} -Wall -o $@ helloworld.o
clean:
                 rm -f ${PROGS} *.o

```

rename your main.c to helloworld.c

---

