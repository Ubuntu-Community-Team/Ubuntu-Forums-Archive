---
title: "compiling a custom kernel for g4 the ubuntu way ???"
date: 2006-10-29
forum: Apple PPC Users
---

### Post by techrush on 2006-10-29
id like to update my powerbook g4 thats running edgy to the latest kernel (2.6.18.1 i believe). ive found several tutorials for doing this on x86 machines but im not sure how much of this transfers over to the powerpc platform. 

the main point that seem to be incompatible is yaboot(ppc) vs grub/lilo(x86).
ive tried messing around with yaboot before and it seems a lot more cryptic to configure than grub so im hesitant to try too tackle this issue myself. 

what im basically looking for is a howto or tutorial on building my own kernel the ubuntu way.

any help would be appreciated!

---

### Post by APU on 2006-10-30
You do not have to touch the yaboot.conf in any way.


The following steps will help
* Download the Kernel sources

* Unpack them into /usr/src (you might also create a symlink /usr/src/linux that always points to your current kernel source)

* Configure the Kernel as you like

* Then use make-kpkg to build the kernel -> This is the important step since it will also create suitable .deb packages that you can install with "sudo dpkg -i yourNewKernelPackage.deb"

In this last step, the symlinks to the current and the last kernel on your machine are adapted in a way that a normal boot boots your new kernel. If you type in "old" at the yaboot prompt early in your boot process you will use the previous kernel again.

This is done completely automatically. Look at the symlinks in the /boot directory before you install anything and try to understand their purpose. They are laid out so that you don´t have to change anything in the yaboot.conf if yo do not want something special (like a third boot option).

Yust as a hint: I always used the following line to compile the kernel with make-kpkg:

"sudo make-kpgk --initrd --append_to_version MyOwnKernel --revision=1"

Try to find out more about which tools you need to compile the kernel in the ubuntu wikis. I did found everything there but do not have any links at hand. Obviously you need make-kpkg, but there are some more things necessary.

By the way - yaboot configuration is pretty straightforward. Just look at the provided config file in /etc and read the manpage of yaboot. I was able to do this when I still was very much a Mac-only user some years back ;-)

---

