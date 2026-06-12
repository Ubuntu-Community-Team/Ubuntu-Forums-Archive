---
title: "NDIS-wrapper..and..Wireless Cards. :/"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Quae on 2007-06-16
I was following the instructions of KevDog (I think it was..) in a different topic, since the guy had the same issue as I did:[COLOR="DarkOrange"] I can't get my wireless card recognized. [/COLOR](01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

But, before that, [COLOR="DarkOrange"]I can't find the damned ndiswrapper program[/COLOR], which, according to the help file, was supposed to be included on my Ubuntu CD (Fiesty, 7.04)..does it not come with the downloaded .iso, or what? And why can't they have it as a package, instead of having to source install it yourself? Anyway. I'm still at trying to get ndiswrapper and, if necessary/easier, ndisgtk on my system.


I extracted ndiswrapper-1.47.tar.gz on my desktop, in a folder of the same name & distro (minus the .tar.gz, obvious.) and [COLOR="Red"]'make distclean'[/COLOR] looks like it went OK. 


However, things went squirrelly with [COLOR="Red"]'make'[/COLOR]:
```
  
kate@Rinukusu:~/Desktop/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/kate/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/kate/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/kate/Desktop/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/kate/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/kate/Desktop/ndiswrapper-1.47/utils'
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
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/kate/Desktop/ndiswrapper-1.47/utils'
make: *** [all] Error 2
kate@Rinukusu:~/Desktop/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/kate/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/kate/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/kate/Desktop/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/kate/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/kate/Desktop/ndiswrapper-1.47/utils'
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
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/kate/Desktop/ndiswrapper-1.47/utils'
make: *** [all] Error 2
kate@Rinukusu:~/Desktop/ndiswrapper-1.47$ 
```

I am not a Linux guru. I have not clue what exactly this means, and how I fix it.

There's almost nothing more frustrating than having to reboot your system into Windows just so you can post that you can't get online via Linux, and then back to Linux to try something else you researched that doesn't end up working. ](*,) I need to get a laptop. 


Sorry, a bit of ranting in there. Spent the last few hours trying to get this figgered out, and it seems Ubuntu hates me. Any help/words of comfort/chocolate?

---

### Post by PartisanEntity on 2007-06-16
Unfortunately ndiswrapper was taken off the Feisty CD, it used to be on all others.

However it is still in the repos, you can install it through the terminal very easily by doing:

```
sudo apt-get ndiswrapper-utils
```

---

### Post by econobeing on 2007-06-16
did you make sure to do these steps before you tried building it?

update the apt list:
```
sudo apt-get update
```

get stuf needed to build programs:
```
sudo apt-get install build-essential
```

get linux headers:
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by Quae on 2007-06-16
> **PartisanEntity said:**
> 
However it is still in the repos, you can install it through the terminal very easily by doing:

```
sudo apt-get ndiswrapper-utils
```

Not so easily. I entered the above, and got: ```
kate@Rinukusu:~$ sudo apt-get ndiswrapper-utils
E: Invalid operation ndiswrapper-utils
```



> **econobeing said:**
> did you make sure to do these steps before you tried building it?

update the apt list:
```
sudo apt-get update
```

This requires internet access, yes? I got a bunch of error messages because I couldn't resolve us.archive.ubuntu.com. Duh. Because I need ndiswrapper to get my Wireless card recognized, and I don't have a wired line that reaches my PC.



> **econobeing said:**
> get stuf needed to build programs:
```
sudo apt-get install build-essential
```  Done, it seemed to go well.

> **econobeing said:**
> get linux headers:
```
sudo apt-get install linux-headers-`uname -r`
``` Done, but it seems I'm up to date: 'For this one, 'linux-headers-2.6.20-15-generic is already the newest version.''.


[B]Someone should update the Feisty Helpfile to reflect the changes regarding ndiswrapper, since it does tell you how to install the package when you try to use ndiswrapper as a command, saying:
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common'


But when you type the above command, you get
```
kate@Rinukusu:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
```[/B]


And..I'm still without ndiswrapper. No one has it as just a downloadable package? I find this hard to believe.

Is there a way I can update/download the repository files via Windows, then just move it to Ubuntu?

---

### Post by Quae on 2007-06-17
Erm. I don't know if I'm supposed to bump up the post or what.

Problem still stands.

---

### Post by Seisen on 2007-06-17
It should be 

```
sudo apt-get install ndiswrapper-utils
```

---

### Post by Quae on 2007-06-17
> **Seisen said:**
> It should be 

```
sudo apt-get install ndiswrapper-utils
```

Tried that too, but I still get:

```
 kate@Rinukusu:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils
```

It's not on the Feisty CD, apparently, and it's not on my system. So, without an internet connection via Ubuntu, and with the above  (previous post in thread) errors when I tried to install it from source, how am I supposed to get ndiswrapper?

---

### Post by nickaj on 2007-06-18
At [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482), it looks like you can download a .tar.gz package of ndiswrapper, so you could dowload it on another computer and move it over with a memory stick or something.

---

### Post by Quae on 2007-06-18
> **nickaj said:**
> At [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482), it looks like you can download a .tar.gz package of ndiswrapper, so you could dowload it on another computer and move it over with a memory stick or something.

> **Quae said:**
> I extracted ndiswrapper-1.47.tar.gz on my desktop, in a folder of the same name & distro (minus the .tar.gz, obvious.) and [COLOR="Red"]'make distclean'[/COLOR] looks like it went OK. 


However, things went squirrelly with [COLOR="Red"]'make'[/COLOR]:
```
  
kate@Rinukusu:~/Desktop/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/kate/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/kate/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/kate/Desktop/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/kate/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/kate/Desktop/ndiswrapper-1.47/utils'
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
../driver/loader.h:24: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:95: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:96: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:160: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:178: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:178: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:205: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:217: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:217: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:221: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:222: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:224: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:232: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:249: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:249: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:251: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:259: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:267: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:271: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:280: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:344: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:346: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:348: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:355: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:367: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:370: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:370: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:373: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:367: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:419: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:419: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:426: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:427: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:429: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:464: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:464: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:473: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:473: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:489: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:489: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:489: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:490: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:495: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:511: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:511: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:517: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:527: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:542: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:549: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:590: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/kate/Desktop/ndiswrapper-1.47/utils'
make: *** [all] Error 2
kate@Rinukusu:~/Desktop/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/kate/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/kate/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/kate/Desktop/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/kate/Desktop/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/kate/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/kate/Desktop/ndiswrapper-1.47/utils'
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
../driver/loader.h:24: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:95: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:96: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:160: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:178: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:178: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:205: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:217: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:217: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:221: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:222: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:224: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:232: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:249: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:249: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:251: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:259: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:267: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:271: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:280: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:344: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:346: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:348: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:355: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:367: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:370: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:370: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:373: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:367: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:419: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:419: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:426: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:427: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:429: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:464: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:464: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:473: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:473: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:489: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:489: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:489: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:490: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:495: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:511: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:511: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:517: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:527: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:542: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:549: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:590: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/kate/Desktop/ndiswrapper-1.47/utils'
make: *** [all] Error 2
kate@Rinukusu:~/Desktop/ndiswrapper-1.47$ 
```

Been thar. Done that. Can't get anyone to tell me exactly what the above **means** and how I remedy it.

---

### Post by Quae on 2007-06-18
..anyone?

It's sort of irritating to get instructions, and then be dropped when those instructions didn't turn out the results as planned.

---

### Post by Quae on 2007-06-18
If I were to create a CD for a non-Fiesty Ubuntu version that had the ndiswrapper package on it, and had the CD in the drive when I booted Fiesty, would I be able to find and install that package from the non-Feisty CD onto Fiesty?

---

### Post by Billy the Kid on 2007-06-18
Have you looked here: [http://ubuntuforums.org/showthread.php?p=1741197#post1741197](http://ubuntuforums.org/showthread.php?p=1741197#post1741197)?
The instructions are intended for the Dell Inspiron E1505, but I've found that they 
are applicable to almost any system.

---

### Post by gcos7 on 2007-06-18
Well, I'm a novice a Linux myself, but I have a suggestion:

Using Windows, where you have an internet connection, download an older version of the Ubuntu live cd - such as 6.10.  It will have ndiswrapper in it.  Just burn another CD with that image, but DON"T boot with it - let LInux boot with 7.04.  Then put the CD in the drive and run system/administration/synaptic package manager.  When the package manager is up, click on edit and then on add CD.  I think you then have to do a reload in the package manager.  Now search for ndiswrapper and install it from the CD.  Hopefully that will work.

I, along with countless others, have had to fight the ndiswrapper fight to get our wireless cards working.  I tried installing Ubuntu from the 7.04 live cd and ran into problems, so I installed it from the 6.10 live cd and did the updates.

Another thing that someone on this forum mentioned was a big help to me as well - install either network-manager or network-manager-gnome.  That helped me immeasurably.  

I hope this helps in some way.  You may even want to install 6.10 first, since this appears to be a new installation, install ndiswrapper, etc., while in it, then go through the update process to update to 7.04.  I even screwed up enough that I had to reload Linux more than once and it was always easier starting with 6.10 and then going through system/administration/update manager.:D

---

### Post by Quae on 2007-06-18
I'll try that, then.

---

### Post by misconfiguration on 2007-06-19
> **Quae said:**
> I'll try that, then.

Since you don't have teh internets on the rig you want to work on, I assume you have a flash drive? Download the following packages and slap them on a flash drive.

[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)

[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)

[http://packages.ubuntu.com/edgy/net/ndisgtk](http://packages.ubuntu.com/edgy/net/ndisgtk)

Copy the files to your /home DIR and start to unpack
```

sudo dpkg -i ndiswrapper-common_*.deb

sudo dpkg -i ndiswrapper-utils*.deb

sudo dpkg -i --force-depends ndisgtk_*.deb

```

Or if you want to physically move your machine and dl and install the stuff from the repos, do this..

```
sudo apt-get install ndiswrapper-common

sudo apt-get install ndisgtk

sudo apt-get install ndiswrapper-utils-1.9

```

Let me know if this helps any =Þ

---

### Post by rebelfox-uk on 2007-06-19
I'm with you on that one Quae, and were not alone. 
In fact even all this feisty, dapper, etc. is confusing the hell out of me. 
There is no mention of this on the ubuntu home page nor the page where you download
the software, I still have no idea which version I'm running.
But my main problem is no wireless connection and there seems to be no answer as to how to install
ndiswrapper...probably a load of techies having a right old chortle eh?

---

### Post by misconfiguration on 2007-06-20
My suggestions didn't work, there are two scenarios. I find that hard to believe my second method works fine, but I have teh internets.

---

### Post by theDaveTheRave on 2007-07-16
Your best bet is I think ultimately to do some moving of equipment to enable you to get your system hard wired to the net!

the Dapper /  Fiesty thing you will get used to.

Ubuntu 6.06 / 6.10 are both Dapper

Ubuntu 7.04 etc are all Fiesty

I do seem to recall seeing others out there Hoary hedhog is I think and earlier version, and there is a "G" one as well, but I'm not sure if that is the "I'm a mad techie and want to see if I can break my computer and put it together again" newer alpha version or an older on!

Either good luck.

Dave

---

### Post by theboomboomcars on 2007-07-17
I can't help you on the make problem but in the documentation pages is says how to install a program from a package if you have another computer hooked to the internet.
Here is a link:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I cannot get my rtl8185 card to work with ndiswrapper, but it works with the native driver.  I just had to unblacklist it.  

To do that use:
sudo nano /etc/modprobe.d/blacklist
towards the end of the file the r818x will be listed put a # in front of it to make the black list ignore it.

Then you can use
sudo modprobe r818x 
to load the driver without rebooting.

Hopefully that will work for you.

---

