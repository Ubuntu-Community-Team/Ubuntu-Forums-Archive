---
title: "Cannot Install Ndiswrapper 1.38"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by M0rThden on 2007-03-08
Hey,

My wireless card is only supported with nidswrapper 1.38. The 'make distclean' works perfectly but the make command doesnt. the ndiswrapper that can be install with the synaptic isnt comatible with my card. My card is the WPC54GX4.

here is the error message, I cut alot of it out because its long.

```
root@shatcher-laptop:/home/shatcher/Desktop/ndiswrapper-1.38# make
make -C driver
make[1]: Entering directory `/home/shatcher/Desktop/ndiswrapper-1.38/driver'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/shatcher/Desktop/ndiswrapper-1.38/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  LD      /home/shatcher/Desktop/ndiswrapper-1.38/driver/built-in.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/crt.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/hal.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/iw_ndis.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/loader.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/ndis.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/ntoskernel.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/ntoskernel_io.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/pe_linker.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/pnp.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/proc.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/rtl.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/wrapmem.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/wrapndis.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/wrapper.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/usb.o
  CC [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/divdi3.o
  LD [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/shatcher/Desktop/ndiswrapper-1.38/driver/ndiswrapper.mod.o
  LD [M]  /home/shatcher/Desktop/ndiswrapper-1.38/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: Leaving directory `/home/shatcher/Desktop/ndiswrapper-1.38/driver'
make -C utils
make[1]: Entering directory `/home/shatcher/Desktop/ndiswrapper-1.38/utils'
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
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’

```

If i need to post more i can

Thanks

---

### Post by Bachstelze on 2007-03-08
Do you have *build-essential* installed ? It compiled perfectly here - but I'm running a 2.6.20 kernel...

---

### Post by M0rThden on 2007-03-08
no i dont belive i have that installed. Let me try to install it and lets see if that changes anything.

Thanks

---

### Post by M0rThden on 2007-03-08
Yea that seemed to do the trick. Gonna remember that one.


Thanks again

---

