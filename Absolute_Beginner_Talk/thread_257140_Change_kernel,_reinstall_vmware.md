---
title: "Change kernel, reinstall vmware?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by rcatman on 2006-09-14
My CPU is a AMD Duron 750mhz.

I installed kubuntu 6.06.1 LTS and of course it is the i386 kernel. I've noticed its much much slower than it is on my other computer. So i've been searching online and found out that I need to install the k7 kernel. The k7 kernel for athlons and durons (not dual processor).

I know I can always come back to the i386 kernel if needed, but when I install the k7 kernel would vmware work in the k7 kernel?

During the installation of vmware i had to point to where the kernel headers were located. Now, because I'm switching kernels I'd think that it would have to point to where the new kernel headers are (k7 header files). Should and how do i uninstall vmware and the winxp installation?

I dont have a video card so i dont need to install the restricted modules. 

All i need to type to install is:
sudo apt-get install linux-k7 linux-headers-k7

right?

I'm scared to mess anything up. Things are slow, but I have them the way i want. What does everyone suggest?

---

### Post by yota on 2006-09-14
You are right: vmware uses 2 kernel modules (vmmon and vmnet) to interact with the system.
If you change your kernel those module will be missing and vmware will stop working.
Anyway you don't have to reinstall vmware: just launch the configuration script from a terminal and it will generate the modules for the current kernel; so install it first, with its headers as you said, then boot up with it and finally launch from a terminal: 
```

sudo vmware-config.pl

```

Hope this helps.

---

### Post by rcatman on 2006-09-14
wow, thank you!

---

