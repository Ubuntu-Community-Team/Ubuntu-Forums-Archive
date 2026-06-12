---
title: "Compiling a 2nd kernel"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-06-03
Hi,

I already have compiled one cusome kernel that I'm using now. I'd like to compile another one yet keep the one I'm using now and therefore have a question about that. To compile my current kernel I first downloaded Ubuntu kernel sources (linux-source-2.6.20). That was at he time of kernel 2.6.20-15. Then in /usr/src I created a symlink from the folder "linux-2.6.20" to "linux" and compiled the kernel from folder "linux".

Now that kernel 2.6.20-16 is released, I want to patch it and compile it but keep my patched 2.6.20-15 kernel (that has been installed from the /usr/src/linux folder). If I redownload linux-source-2.6.20 (which now contains kernel 2.6.20-16) and extract it this will probably overwrite the old "linux-2.6.20" folder and thus the symlinked "linux" folder will contain 2.6.20-16 and no more 2.6.20-15! So how should I do? Should I download linux-source-2.6.20 and then extract it under linux-2.6.20-16 and then create a symlink to linux2 or something in order to compile the kernel?? If I delete linux-2.6.20 and linux folders in /usr/src, will this remove the modules?

By the way why do most guide recommend to create a symlink from the kernel source to a folder called "linux"? Isn't it preferable to compile the kernel directly from its source folder (like linux-2.6.20)??

---

### Post by plcdfa on 2007-06-03
Why do you want to keep the 2.6.20-15  kernel sources?  You have already compiled a working kernel from it, and you're very unlikely to need it again. The kernel itself went to /boot and the modules to /lib/modules. You don't need the sources to run the kernel. Just delete the directory and then download the newer source package. Your new kernel will also go to /boot and the modules to /lib/modules (to a different subdirectory.) You can configure the grub menu so that both kernels can be booted. (In fact it'll be configured that way automatically by grub-install if you run it after compiling the kernel.)
As for the last question: I honestly don't know. :) I've never created  a symlink and still my compilations worked out ok.

---

### Post by kilou on 2007-06-03
I don't want to keep the 2.6.20-15 that originally came with Feisty. I want to keep that 2.6.20-15 that I patched afterwards and that I use currently. So basically the source folders in /usr/src are useless once the kernel is compiled?? But I should still keep the headers folder in /usr/src or not??

It's nice if I can just delete the source folders in /usr/src and start with a new kernel source :)

---

### Post by plcdfa on 2007-06-04
You can delete everything from /usr/src.

---

