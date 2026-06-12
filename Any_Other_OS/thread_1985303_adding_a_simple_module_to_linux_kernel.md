---
title: "adding a simple module to linux kernel"
date: 2012-05-23
forum: Any Other OS
---

### Post by solgab on 2012-05-23
Hello,
I'm trying to upload a simple module to linux kernel.
I want to know where to put the makefile and the module file, in which directory.
I'm using linux version 3.0.0.
I have an example for makefile but it fits old version of linux : 
   KERNELDIR = /usr/src/linux-2.4.18-14custom
   include $(KERNELDIR)/.config
   CFLAGS = -D__KERNEL__ -DMODULE –I$(KERNELDIR)/include –O -Wall
   all: testModule.o
What should i change in this makefile (except fo the linux version) in  order to compile the module it in the current linux version (3.0.0)?
My module is only printing a Hello string,nothing special.

Thanks!!!:wink:
Olga.

---

### Post by nothingspecial on 2012-05-23
Duplicate of this

[http://ubuntuforums.org/showthread.php?t=1985304](http://ubuntuforums.org/showthread.php?t=1985304)

Closed

---

