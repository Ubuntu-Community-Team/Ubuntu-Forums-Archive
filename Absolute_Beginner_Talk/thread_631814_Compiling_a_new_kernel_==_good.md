---
title: "Compiling a new kernel == good?"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-12-04
While I've searched this forum and other places on the web for answers to unrelated problems, I've come across a lot of things about re-compiling kernels.  Unfortunately for me, these were mainly "HOWTOs" and not "WHYFORs."  There was some who claimed it was for better speed and stability, and others who claimed that, unless you had a reason to compile a new kernel, there was no need...  But how does one know if one -should- compile their own kernel?  What exactly are the benefits, anyway?

Searching this forum, I've found several well-written HOWTOs on compiling kernels... but none ever really talked about why you should do it, or what you would gain from doing so.  I'd really like to know.  Maybe I could improve my system's performance, after all.  Then again, the kernel's supposed to be an Important Thing, right, so I don't want to go changing it if I don't need to, especially if I'll make it worse, heh.

---

### Post by PeterJS on 2007-12-04
There are pretty much two reasons to roll your own kernel:
1)Getting support of a driver that isn't included
2)Squeezing every ounce of power out of a system with optimizations specific to your needs


The first reason really doesn't hold any weight under debian and ubuntu systems, as the debian method of building the kernel is to build everything as a module. So if the driver exists it can be loaded when the system runs, with no need to recompile.

As to the second point the modular nature of the kernel as built by ubuntu means that you're not going to optimize much more for RAM usage, they made everything they could a module, and a module will only be loaded if it's needed. For CPU and IO usage the optimizations people make usually aren't all that great just a couple of percentage points. If the optimizations in the desktop kernel don't meet your needs look in to the server kernel.

---

### Post by kevdog on 2007-12-04
I second the points above, however if you are really interested in how linux runs, and about modules, and just how the kernel can be configured -- I say go for it.  It will teach you a lot, and some of the discussions of the forums will just "make sense" with this added knowledge.

---

### Post by SOULRiDER on 2007-12-04
Compiling a kernel can help you learn a lot about how things work, but it can also be a big problem. Unless you really know what youre doing I say don't compile your own kernel.

While is is true that compiling your own kernel may speed things up I dont think Ubuntu is the best distro to do that with. IMHO if you want to learn more aobut how everything works at a lower level, install Gentoo alongside with Ubuntu and tweak it to your needs.

---

