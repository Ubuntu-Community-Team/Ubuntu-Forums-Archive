---
title: "has anyone noticed alot of things have gotten broken with the lastest rounds of updat"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-17
i installed alot of software under the old kernel upgraded to the new kernel and alot of my apps no longer work properly vmware server and k9copy just to name a few..they work fine as long as i select the old kernel on bootup..I also compiled a new kernel and that does the samething alot of apps no longer work..So basically my question is everytime a kernel is updated do u also have to reinstall apps as well?

---

### Post by givré on 2006-06-17
You compile for a kernel, so when you have a new kernel, you have to compile again this modules

EDIT: it's not a matter of apps, it's a matter of module, or driver that you compile for the kernel. Ex: vmware need some specific module, and so they will not work for a new kernel

---

### Post by mscman on 2006-06-17
I think VMWare is installed and compiled with the kernel.  This probably explains the breakage you're seeing when you upgrade the kernel; the kernel it was expecting isn't actually the one you're using.  I'm not sure about the other program.

Kernel upgrades tend to break some stuff, as some programs are dependent on the kernels.

---

### Post by lime4x4 on 2006-06-17
so what is the best way to fix it then?? Just reinstall the apps that no longer work?

---

