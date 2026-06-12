---
title: "vpn client install/kernel source"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by 77midget on 2008-02-07
hello all-just made move to linux (Ubuntu 7.10) on a spare HD for my laptop, a Dell Precision M70. I am on day 3, and so far so good, got the NVidia card working, and the wireless card too, but I have issues with the VPN client (I need it since this is a work machine). My install package asks for binary install, which defaults to /usr/local/bin, and I have left that, and it asked for kernel source directory since it needs the headers for compilation, for which I have come up with /usr/src/linux-headers-2.6.22-14-generic , as that is the kernel that my install is using. On install, I am getting some errors, and it seems that the install is not compiling the necessary bits to the kernel. Below is the relevant install log parts. as when I try to start it, it throws kernel errors Any thoughts? Am I doing something wrong?

thx in advance

 Making module
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /vpnclient/linuxcniapi.o
  CC [M]  /vpnclient/frag.o
  CC [M]  /vpnclient/IPSecDrvOS_linux.o
  CC [M]  /vpnclient/interceptor.o
/vpnclient/interceptor.c: In function ‘handle_vpnup’:
/vpnclient/interceptor.c:313: warning: assignment from incompatible pointer type
/vpnclient/interceptor.c:337: warning: assignment from incompatible pointer type
/vpnclient/interceptor.c:338: warning: assignment from incompatible pointer type
/vpnclient/interceptor.c: In function ‘do_cleanup’:
/vpnclient/interceptor.c:386: warning: assignment from incompatible pointer type
  CC [M]  /vpnclient/linuxkernelapi.o
  LD [M]  /vpnclient/cisco_ipsec.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: /vpnclient/cisco_ipsec.o(.data+0xb8): Section mismatch: reference to .init.text: (between 'interceptor_dev' and 'interceptor_notifier')
WARNING: could not find /vpnclient/.libdriver.so.cmd for /vpnclient/libdriver.so
  CC      /vpnclient/cisco_ipsec.mod.o
  LD [M]  /vpnclient/cisco_ipsec.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
Copying module to directory "/lib/modules/2.6.22-14-generic/CiscoVPN".

---

### Post by finer recliner on 2008-02-09
when installing from source, most of the time you need to run the configure script before running 'make'. did you do this?

```
./configure
```
make sure the configure scripts completes successfully. otherwise you probably have dependency errors.

---

### Post by 77midget on 2008-02-09
hmm. the client install is already compiled, you just need to run it. I do suspect that there is a dependency issue wit my kernel headers/source tho, as the install seems to be failing when it tries to recompile the kernel.

---

