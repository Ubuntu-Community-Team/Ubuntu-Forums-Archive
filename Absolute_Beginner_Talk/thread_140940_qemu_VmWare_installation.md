---
title: "qemu/ VmWare installation"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-03-07
Hi guys/gals
                after following the informative HowTo : - [http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware)

I tried to configure qemu and straight away ran into prob.

```
ERROR: QEMU requires SDL or Cocoa for graphical outputTo build QEMU with graphical output configure with --disable-gfx-check Note that this will disable all output from the virtual graphics card. 
jeremy@UBUNTU:~/temp/qemu-0.7.1$./configure --disable-gfx-check

```

Managed to enter command to configure, then the following error at the bottom of terminal screen

```
/home/jeremy/temp/qemu-0.7.1/target-i386/ops_sse.h:574: confused 
by earlier errors, bailing out
make[1]: *** [op.o] Error 1
make[1]: Leaving directory `/home/jeremy
/temp/qemu-0.7.1/i386-user'
make: *** [all] Error 1
jeremy@UBUNTU:~/temp/qemu-0.7.1$ wine qemu-img.exe create -f
 vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
wine: could not load L"C:\\Windows\\
System\\qemu-img.exe": Module not found

```

Any way I can fix this, or an easier way to use Windows programs such as visio with Ubuntu?
Ta in advance
:D

---

### Post by carverj on 2006-03-08
ok, I think I have bypassed this problem :confused:  and encountered a new one.
am trying to configure qemu and it doesn't like gcc 4.x

```
jeremy@UBUNTU:~/temp/qemu-0.8.0$ ./configure gcc 3.3
ERROR: "gcc" looks like gcc 4.x
QEMU is known to have problems when compiled with gcc 4.x
It is recommended that you use gcc 3.x to build QEMU
To use this compiler anyway, configure with --disable-gcc-check

```

Should I remove gcc 4.x ? because a few programs seem to be dependant on it!
:-? 
Thanks guys/gals

---

### Post by jazzuban on 2007-01-27
You need SDL and gcc 3.4 :

```
sudo apt-get install libsdl-dev gcc-3.4 cpp-3.4
```

and tell configure to use gcc 3.4

```
sh ./configure --gcc=gcc-3.4   
```

---

### Post by Jussi01 on 2007-01-27
IMHO, I would recommend using virtualbox - it runs faster and is lots easier to install. [www.virtualbox.com](www.virtualbox.com)

---

