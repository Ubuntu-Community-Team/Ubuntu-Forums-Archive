---
title: "Need help when trying to &quot;make&quot; ndiswrapper - 1.38"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by j2p2f2 on 2007-03-12
Ive been trying to install the new ndiswrapper because i need it to run my wg111 v2. I have the drivers and everything, but if i use the ndiswrapper -i [driver location] it says ndiswrapper is not installed. I went out and got the new version because im using edgy and it wont make the installer. When i run make in the directory, I get a ton of errors that I have no clue how to fix. Im assuming im missing a package build the files with?

I have downloaded and tried to install:
Build-essentials
Libgcc
gcc
make-3.81
libc6
ndiswrapper-common

all give newer version error.

I did have one thing i understood, which was ai needed libc-dev | libc6-dev so i went to google and downloaded the headers, but i dont know if i got the right file.

Here is the error it gave me from the "make" command.

```

farkas@Compaq-Jeff-Linux:~/Desktop/ndiswrapper-1.38$ make
make -C driver
make[1]: Entering directory `/home/farkas/Desktop/ndiswrapper-1.38/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/farkas/Desktop/ndiswrapper-1.38/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/farkas/Desktop/ndiswrapper-1.38/driver'
make -C utils
make[1]: Entering directory `/home/farkas/Desktop/ndiswrapper-1.38/utils'
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
make[1]: Leaving directory `/home/farkas/Desktop/ndiswrapper-1.38/utils'
make: *** [all] Error 2
farkas@Compaq-Jeff-Linux:~/Desktop/ndiswrapper-1.38$ 

```

Thanks for any help you can give :)

---

### Post by benfindlay on 2007-03-13
may be a daft question, but did you go into the directory and do ```
./configure
``` first?

---

### Post by pab0pab0 on 2007-03-21
I just had this problem too. You need to add some C libraries and headers. If you go to the package manager and scroll almost to the bottom you should see something along these lines. Click to install it and then make should work alright!

---

