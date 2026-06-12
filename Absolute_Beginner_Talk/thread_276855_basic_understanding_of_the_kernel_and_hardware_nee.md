---
title: "basic understanding of the kernel and hardware needed"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-10-13
I have a Hauppauge 150 tuner card, and would like to use vmware. As I understand it, I need to compile the kernel with specialized modules for both instances to work

I followed a how-to for the ivtv module once before and eventually got it to work – although it took me an entire afternoon to complete and debug. I’ve yet to try to compile for vmware – but will be giving it a shot tonight.

It would also be nice to optimize the kernel by making it more specific to my hardware – but for now, I’m really just interested in getting my hardware working.

Rather than rely on how-to’s, which often vary in methods, kernels, distributions and effectiveness – I would prefer to understand the fundamentals so that I can think my way through it on my own.

As such, what resource (book, website) would you suggest to get me started? How does xconfig fit into the picture? What are the fundamental steps in compiling a kernel (e.g. download source code and modules, makefile, compile, put new kernel into boot folder, and edit grub)? 

I am starting to see this as a critical skill if I am going to use Linux.

Many thanks,

Sean

---

### Post by mahy on 2006-10-13
> **Episteme said:**
> As such, what resource (book, website) would you suggest to get me started? How does xconfig fit into the picture? What are the fundamental steps in compiling a kernel (e.g. download source code and modules, makefile, compile, put new kernel into boot folder, and edit grub)? 

I am starting to see this as a critical skill if I am going to use Linux.


Start with reading [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel) and check out all the links. The basic steps are:

1.) download, unpack, change current directory into it
2.) make menuconfig - modify whatever you want to
3.) make
4.) make modules
5.) make modules_install
6.) make install
7.) reboot (if you have GRUB, it'll automatically appear in the menu)

/* i left out the sudo */

Kernel compiling is becoming less and less necessary for running Linux. I've been using Linux for several years already, but i absolutely loathe kernel compiling and i'm trying to stick with packaged kernels at all costs. That's the reason (along with brilliant package management and rich repositories) why i love Ubuntu.

---

