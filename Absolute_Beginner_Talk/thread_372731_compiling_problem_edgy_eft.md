---
title: "compiling problem edgy eft"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by DarkEye on 2007-02-28
Hi everyone,

I just installed Ubuntu "Edgy Eft" 6.10 on my laptop (pretty old one), but I can't get my wireless adapter to work. I tried to install ndiswrapper 1.37, put it on the laptop through my memory stick, but when i try to "make" it it shows this:

```
root@stef:/home/stef/Desktop/ndiswrapper-1.37# make
make -C driver
make[1]: Entering directory `/home/stef/Desktop/ndiswrapper-1.37/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/stef/Desktop/ndiswrapper-1.37/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/stef/Desktop/ndiswrapper-1.37/driver'
make -C utils
make[1]: Entering directory `/home/stef/Desktop/ndiswrapper-1.37/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before â€˜size_tâ€™
loadndisdriver.c: In function â€˜load_fileâ€™:
loadndisdriver.c:67: error: â€˜size_tâ€™ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected â€˜;â€™ before â€˜sizeâ€™
loadndisdriver.c:68: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:71: warning: implicit declaration of function â€˜basenameâ€™
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function â€˜openâ€™
loadndisdriver.c:73: error: â€˜O_RDONLYâ€™ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â€˜syslogâ€™
loadndisdriver.c:75: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:75: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â€˜strerrorâ€™
loadndisdriver.c:75: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:76: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function â€˜fstatâ€™
loadndisdriver.c:81: warning: implicit declaration of function â€˜closeâ€™
loadndisdriver.c:84: error: â€˜sizeâ€™ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function â€˜mmapâ€™
loadndisdriver.c:86: error: â€˜PROT_READâ€™ undeclared (first use in this function)
loadndisdriver.c:86: error: â€˜MAP_PRIVATEâ€™ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: â€˜MAP_FAILEDâ€™ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function â€˜strncpyâ€™
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:95: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:96: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:69: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜parse_setting_lineâ€™:
loadndisdriver.c:109: warning: implicit declaration of function â€˜isspaceâ€™
loadndisdriver.c:115: warning: implicit declaration of function â€˜strchrâ€™
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function â€˜strchrâ€™
loadndisdriver.c:115: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:117: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:117: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:118: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function â€˜strlenâ€™
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
loadndisdriver.c: In function â€˜read_conf_fileâ€™:
loadndisdriver.c:150: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:151: error: â€˜FILEâ€™ undeclared (first use in this function)
loadndisdriver.c:151: error: â€˜configâ€™ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function â€˜lstatâ€™
loadndisdriver.c:158: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:158: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:158: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:160: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function â€˜sscanfâ€™
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function â€˜sscanfâ€™
loadndisdriver.c:179: warning: implicit declaration of function â€˜fopenâ€™
loadndisdriver.c:179: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function â€˜fgetsâ€™
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:206: warning: implicit declaration of function â€˜fcloseâ€™
loadndisdriver.c:150: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜load_bin_fileâ€™:
loadndisdriver.c:218: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:218: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function â€˜tolowerâ€™
loadndisdriver.c:222: warning: implicit declaration of function â€˜chdirâ€™
loadndisdriver.c:223: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:225: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:233: warning: implicit declaration of function â€˜ioctlâ€™
loadndisdriver.c:233: warning: implicit declaration of function â€˜_IOWâ€™
loadndisdriver.c:233: error: expected expression before â€˜structâ€™
loadndisdriver.c: In function â€˜load_driverâ€™:
loadndisdriver.c:250: error: â€˜DIRâ€™ undeclared (first use in this function)
loadndisdriver.c:250: error: â€˜driver_dirâ€™ undeclared (first use in this function)
loadndisdriver.c:252: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:256: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:256: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:258: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:260: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function â€˜opendirâ€™
loadndisdriver.c:268: warning: implicit declaration of function â€˜mallocâ€™
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function â€˜mallocâ€™
loadndisdriver.c:272: warning: implicit declaration of function â€˜memsetâ€™
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function â€˜memsetâ€™
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:281: warning: implicit declaration of function â€˜readdirâ€™
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function â€˜statâ€™
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function â€˜S_ISREGâ€™
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function â€˜strcasecmpâ€™
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function â€˜strcpyâ€™
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function â€˜strcpyâ€™
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:319: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable â€˜statbufâ€™
loadndisdriver.c:345: error: expected expression before â€˜structâ€™
loadndisdriver.c:347: warning: implicit declaration of function â€˜closedirâ€™
loadndisdriver.c:349: warning: implicit declaration of function â€˜freeâ€™
loadndisdriver.c:356: warning: implicit declaration of function â€˜munmapâ€™
loadndisdriver.c:356: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:356: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:358: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:358: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c: In function â€˜get_deviceâ€™:
loadndisdriver.c:368: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:371: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:371: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:374: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:375: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function â€˜snprintfâ€™
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function â€˜snprintfâ€™
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:368: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜load_deviceâ€™:
loadndisdriver.c:420: error: â€˜DIRâ€™ undeclared (first use in this function)
loadndisdriver.c:420: error: â€˜dirâ€™ undeclared (first use in this function)
loadndisdriver.c:424: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:424: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function â€˜memsetâ€™
loadndisdriver.c:427: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:428: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:430: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:449: error: expected expression before â€˜structâ€™
loadndisdriver.c: In function â€˜get_ioctl_deviceâ€™:
loadndisdriver.c:466: error: â€˜FILEâ€™ undeclared (first use in this function)
loadndisdriver.c:466: error: â€˜proc_miscâ€™ undeclared (first use in this function)
loadndisdriver.c:474: warning: implicit declaration of function â€˜strstrâ€™
loadndisdriver.c:474: warning: incompatible implicit declaration of built-in function â€˜strstrâ€™
loadndisdriver.c:475: warning: implicit declaration of function â€˜strtolâ€™
loadndisdriver.c:475: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:485: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:485: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:490: warning: implicit declaration of function â€˜unlinkâ€™
loadndisdriver.c:491: warning: implicit declaration of function â€˜mknodâ€™
loadndisdriver.c:491: error: â€˜S_IFCHRâ€™ undeclared (first use in this function)
loadndisdriver.c:491: error: â€˜MISC_MAJORâ€™ undeclared (first use in this function)
loadndisdriver.c:492: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:497: error: â€˜O_RDONLYâ€™ undeclared (first use in this function)
loadndisdriver.c: In function â€˜mainâ€™:
loadndisdriver.c:513: warning: implicit declaration of function â€˜openlogâ€™
loadndisdriver.c:513: error: â€˜LOG_PERRORâ€™ undeclared (first use in this function)
loadndisdriver.c:513: error: â€˜LOG_CONSâ€™ undeclared (first use in this function)
loadndisdriver.c:513: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:513: error: â€˜LOG_DEBUGâ€™ undeclared (first use in this function)
loadndisdriver.c:515: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:517: warning: implicit declaration of function â€˜strncmpâ€™
loadndisdriver.c:519: warning: implicit declaration of function â€˜printfâ€™
loadndisdriver.c:519: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
loadndisdriver.c:529: warning: implicit declaration of function â€˜atoiâ€™
loadndisdriver.c:544: warning: implicit declaration of function â€˜atofâ€™
loadndisdriver.c:551: warning: implicit declaration of function â€˜strcmpâ€™
loadndisdriver.c:558: warning: incompatible implicit declaration of built-in function â€˜sscanfâ€™
loadndisdriver.c:592: warning: implicit declaration of function â€˜closelogâ€™
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/stef/Desktop/ndiswrapper-1.37/utils'
make: *** [all] Error 2

```

I searched about this problem online, and I found several threads showing that I might be missing the libc6-dev library ... I tried to download it from multiple sources but it always showed "dependency problem with libc6" so I'm stuck now...

I also read in many places something about build-essential, but I'm really stuck now and any help is welcome :)

thanks in advance,


-DarkEye

---

### Post by DarkEye on 2007-02-28
up...anyone ? this is starting to annoy me :(

---

### Post by zvacet on 2007-02-28
To build-essential
```
sudo aptitude install build-essential
```
and for libc6-dev in firefox search engine find ubuntu packages and type libc6-dev
I hope it helps.

---

### Post by koconnor100 on 2007-02-28
yer basic ubuntu 6.10 has a lot of bugs in it, including that the compiler don't work. 

You ahve to get that ubuntu patch to fix all that up. "easyubuntu" it's called. 

[https://launchpad.net/easyubuntu](https://launchpad.net/easyubuntu)

(edit)
this sticks an option on your applications / system tools menu called easy ubuntu , launch it and just click on all the patches you want. You want pretty much all of it (well...if your video drivers arn't Nvidea you probably don't want the nvidea patch...use common sense)

---

