---
title: "How does one compile a kernel without make-kpkg?"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by randomshinichi on 2006-01-21
I've run into a problem while recompiling my kernel. I configured it fine, and booted it to see if my configuration had any problems with it. I found out that I had neglected to disable some Ftape modules.... and savagefb seems to be causing some corruption in the bottom half of my display (I have savage DRI working). 

I tried to recompile the kernel without these things make menuconfig now shows the proper settings whenever I run that command, but when I make-kpkg and install the resulting deb files, I reboot into the new kernel and always find that those modules are still there. Before uninstalling my current kernel, I always check that the modules directory in /lib/modules does not have a name that resembles the new kernel, so they can't be the modules from the previous kernel build.

So, with that problem explained, how do I install my little kernel? Do I just make && make modules_install and copy the resulting files? If so, why did I have to go through all that kernel_package (make-kpkg) stuff?

---

