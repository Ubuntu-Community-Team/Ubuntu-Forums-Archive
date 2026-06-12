---
title: "Errors while using the make command"
date: 2005-06-12
forum: Absolute Beginner Talk
---

### Post by Hamad on 2005-06-12
I downloaded ndiswrapper-0.11.tar.gz. And i did the following:
```

root@computer:/home/hamad/Downloads # tar zxvf ndiswrapper-0.11.tar.gz
ndiswrapper-0.11/
ndiswrapper-0.11/AUTHORS
ndiswrapper-0.11/ChangeLog
ndiswrapper-0.11/INSTALL
ndiswrapper-0.11/Makefile
ndiswrapper-0.11/README
ndiswrapper-0.11/ndiswrapper.spec.in
ndiswrapper-0.11/version
ndiswrapper-0.11/ndiswrapper.8
ndiswrapper-0.11/utils/
ndiswrapper-0.11/utils/Makefile
ndiswrapper-0.11/utils/ndiswrapper
ndiswrapper-0.11/utils/loadndisdriver.c
ndiswrapper-0.11/utils/ndiswrapper-buginfo
ndiswrapper-0.11/driver/
ndiswrapper-0.11/driver/Makefile
ndiswrapper-0.11/driver/ndiswrapper.h
ndiswrapper-0.11/driver/pe_loader.c
ndiswrapper-0.11/driver/pe_loader.h
ndiswrapper-0.11/driver/ndis.c
ndiswrapper-0.11/driver/ndis.h
ndiswrapper-0.11/driver/hal.c
ndiswrapper-0.11/driver/ntoskernel.c
ndiswrapper-0.11/driver/ntoskernel.h
ndiswrapper-0.11/driver/iw_ndis.c
ndiswrapper-0.11/driver/iw_ndis.h
ndiswrapper-0.11/driver/wrapper.c
ndiswrapper-0.11/driver/wrapper.h
ndiswrapper-0.11/driver/proc.c
ndiswrapper-0.11/driver/misc_funcs.c
ndiswrapper-0.11/driver/divdi3.c
ndiswrapper-0.11/driver/longlong.h
ndiswrapper-0.11/driver/usb.c
ndiswrapper-0.11/driver/usb.h
ndiswrapper-0.11/debian/
ndiswrapper-0.11/debian/Makefile
ndiswrapper-0.11/debian/control.modules
ndiswrapper-0.11/debian/control.utils
ndiswrapper-0.11/debian/copyright
ndiswrapper-0.11/debian/dirs.utils
ndiswrapper-0.11/debian/docs
ndiswrapper-0.11/debian/README.Debian
ndiswrapper-0.11/debian/rules
ndiswrapper-0.11/debian/changelog.template
ndiswrapper-0.11/debian/control.source
ndiswrapper-0.11/debian/postinst.modules
root@computer:/home/hamad/Downloads # cd ./ndiswrapper-0.11
root@computer:/home/hamad/Downloads/ndiswrapper-0.11 # make
make -C driver
make[1]: Entering directory `/home/hamad/Downloads/ndiswrapper-0.11/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/hamad/Downloads/ndiswrapper-0.11/driver'
make: *** [all] Error 2
root@computer:/home/hamad/Downloads/ndiswrapper-0.11 # 

```
I always get an error while using the make command, even while compileing other tar.gz files...
How can i fix this peoblem ?

---

### Post by Xian on 2005-06-12
Just a stab, but do you have the appropriate kernel source installed w/symlink?

---

### Post by Hamad on 2005-06-12
> Just a stab, but do you have the appropriate kernel source installed w/symlink?
Sorry but i didnt understand, do you mean i have to get some package called w/symlink ?

---

### Post by Xian on 2005-06-12
Well, the configure session is stating it can't find the kernel source, so I thought it might be wise to install that on your system via Synaptic if not already present, and then you often have to create a symlink in the /usr/src path to that kernel folder (you may have to untar the kernel source depending on what Synaptic places there) called 'linux'.

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=Hamad]I downloaded ndiswrapper-0.11.tar.gz. And i did the following:
[/QUOTE]

You might not have to compile ndiswrapper. Did you try installing the ndiswrapper-utils package?

[http://packages.ubuntu.com/hoary/misc/ndiswrapper-utils](http://packages.ubuntu.com/hoary/misc/ndiswrapper-utils)

---

### Post by cpmpal on 2007-11-09
uh i have  similar issue with fwcutter but how would someone go about installing it without internet because i have tried ndisgtk,ndiswrapper,and fwcutter(compatible with my card) and all give me an error 1, 2, or both errors during sudo make, make install any ideas either? sorry for saying here din't feel like opening a full new thread.

---

