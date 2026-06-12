---
title: "[SOLVED] Tried Hard But cannot get Wireless Working :("
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by rtr86 on 2007-09-07
Hi all,

I installed Linux Ubuntu on a spare computer yesterday (first time ever using Linux) after lots of reading I am unable to get wireless working. I have been trying to install ndiswapper, below is the code I enterd into the command box. 

 > 
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/rich/Desktop/ndiswrapper-1.47/utils'
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
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/utils'
make: *** [all] Error 2
rich@Rich-Linux:~/Desktop/ndiswrapper-1.47$ make install
make -C driver install
make[1]: Entering directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/rich/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
install: cannot remove `/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make: *** [install] Error 2
rich@Rich-Linux:~/Desktop/ndiswrapper-1.47$ sudo make install
make -C driver install
make[1]: Entering directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/rich/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
/sbin/depmod -a 2.6.20-16-generic -b /
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make -C utils install
make[1]: Entering directory `/home/rich/Desktop/ndiswrapper-1.47/utils'
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
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/utils'
make: *** [install] Error 2
rich@Rich-Linux:~/Desktop/ndiswrapper-1.47$ cd /home/rich/Desktop/WMP54GS_20050406
rich@Rich-Linux:~/Desktop/WMP54GS_20050406$ cd /home/rich/Desktop/WMP54GS_20050406
rich@Rich-Linux:~/Desktop/WMP54GS_20050406$ cd Driversrich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ ndiswrapper -i WMP54GS.infError: no versions of ndiswrapper found!
rich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ ndiswrapper -i WMP54GS.inf



I followed the guide exactly but when i pointed to directory of my .inf files it said ndfiswapper not installed :( 

Please guys, any help will be appreciated!

Thanks

Richard

---

### Post by PeterF on 2007-09-07
To compile the source you need the kernel headers and the build essentials, to me it seems you're missing them. To install search in synaptic or:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```It would have helped if you posted a link to the tutorial you used to see where it went wrong.

---

### Post by gabkdlly on 2007-09-07
Chances are, you don't need to compile anything. Ndiswrapper is in the default Ubuntu kernel. You just need the utilities. Search for ndiswrapper in synaptic. Also, here is some worthwhile reading.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Good luck!

---

### Post by ayenack on 2007-09-07
Am I missing something. What card are you using? Please type these commands in terminal one at a time.

lsusb

lspci

iwconfig

ifconfig

And post the results so that we can see what card you have and your setup:-D

---

### Post by jw5801 on 2007-09-07
The default ndiswrapper included with the feisty kernel is very old and doesn't have the best support for quite a few drivers. 

As was stated above your main issue is that you don't have the build-essential package installed: it contains a lot of C header files you need to compile anything written in C (all those .h files at the top that are said to be missing). It's also a good idea to update your kernel headers before you do this sort of thing (linux-headers-`uname -r` as above). And any time you update them after this you'll need to recompile ndiswrapper, but that doesn't happen often and it only takes a couple of minutes once you work out how to do it.

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
cd /*ndiswrapper-source-directory*
sudo make uninstall #just to make sure there isn't anything left over from any previous attempt
sudo make
sudo make install
cd /*your-windows-driver-directory*
sudo ndiswrapper -i *your-driver*.inf
sudo ndiswrapper -l #to check it installed correctly
sudo modprobe ndiswrapper #to tell the kernel to use the ndiswrapper module
```

Once you've got it all working you'll need to add the ndiswrapper module to the list that run at boottime, else you'll have to run the last command again every time you restart, use the following to do that:
```
sudo -s
echo ndiswrapper >> /etc/modules
exit
```

Lastly a bit of a forum hint: if you want to post alot of terminal output (ie error messages), it's better to enclose it in CODE tags rather than QUOTE tags, that way it takes up alot less thread real-estate. Plus it makes it easier for us since the reason for all the errors and warnings was contained in the first couple of lines! :)

---

### Post by ayenack on 2007-09-07
Does rtr86 need ndiswrapper? What card is in use? Might be supported.

---

### Post by P235 on 2007-09-07
First, welcome to the world of Linux, Richard.  

I do not know which guides you've read, but I suggest you read these two as well:

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926) [For downloading and installing ndiswrapper via make]

[http://ubuntuforums.org/showthread.php?t=361917](http://ubuntuforums.org/showthread.php?t=361917) [Installing ndiswrapper w/ repos]

The basics can be found in these two treads and they've helped me get my wireless card working.  For threads that address particular cards, visit:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by jw5801 on 2007-09-07
> **ayenack said:**
> Does rtr86 need ndiswrapper? What card is in use? Might be supported.

No idea! But he had an issue compiling a program from source so we may as well teach him how to do that while he's here!

---

### Post by rtr86 on 2007-09-07
Firstly. Guys, a HUGE thanks for all the replys :)


> **PeterF said:**
> To compile the source you need the kernel headers and the build essentials, to me it seems you're missing them. To install search in synaptic or:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```It would have helped if you posted a link to the tutorial you used to see where it went wrong.

Hi PeterF,

I am using the latest .iso of ubuntu and never realized the headers needed to be install updated. I have since updated them thanks to you code and the command box now reports back I am updated :)  I therefore managed to complete the installation but i'm still not wireless :(

i'm still uncertain what headers are - I must read up on that.

> **gabkdlly said:**
> Chances are, you don't need to compile anything. Ndiswrapper is in the default Ubuntu kernel. You just need the utilities. Search for ndiswrapper in synaptic. Also, here is some worthwhile reading.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Good luck!
Hi  gabkdlly,

Thanks for link – will read up on that.
Can you tell me what synaptic is please?

 > **ayenack said:**
> Am I missing something. What card are you using? Please type these commands in terminal one at a time.

lsusb

lspci

iwconfig

ifconfig

And post the results so that we can see what card you have and your setup:-D

Hi  ayenack,

Sorry if my first post was a little unclear. I am really new to Linux (never really knew much about it until yesterday) , and i am struggling to get an understanding of everything. I want to connect via my only installed (on this pc) Linksys WMP54GS (Speedbooster edition)

Running the comands give me these outcomes:

```
rich@Rich-Linux:~$ lsusb

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 007: ID 05ac:020c Apple Computer, Inc. 

Bus 001 Device 006: ID 1267:0210 Logic3 / SpectraVideo plc 

Bus 001 Device 005: ID 05ac:1003 Apple Computer, Inc. 

Bus 001 Device 001: ID 0000:0000  

rich@Rich-Linux:~$ lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge

00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge

00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

rich@Rich-Linux:~$ iwconfig

lo        no wireless extensions.



eth1      no wireless extensions.



eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"

          Mode:Managed  Access Point: Invalid   

          RTS thr:off   Fragment thr:off

          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rich@Rich-Linux:~$ ifconfig

eth1      Link encap:Ethernet  HWaddr 00:0C:6E:18:DB:54  

          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::20c:6eff:fe18:db54/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1847 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1872 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:1841564 (1.7 MiB)  TX bytes:229199 (223.8 KiB)

          Interrupt:17 Base address:0xb400 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)



rich@Rich-Linux:~$ 

```



 
> **jw5801 said:**
> The default ndiswrapper included with the feisty kernel is very old and doesn't have the best support for quite a few drivers. 

As was stated above your main issue is that you don't have the build-essential package installed: it contains a lot of C header files you need to compile anything written in C (all those .h files at the top that are said to be missing). It's also a good idea to update your kernel headers before you do this sort of thing (linux-headers-`uname -r` as above). And any time you update them after this you'll need to recompile ndiswrapper, but that doesn't happen often and it only takes a couple of minutes once you work out how to do it.

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
cd /*ndiswrapper-source-directory*
sudo make uninstall #just to make sure there isn't anything left over from any previous attempt
sudo make
sudo make install
cd /*your-windows-driver-directory*
sudo ndiswrapper -i *your-driver*.inf
sudo ndiswrapper -l #to check it installed correctly
sudo modprobe ndiswrapper #to tell the kernel to use the ndiswrapper module
```

Once you've got it all working you'll need to add the ndiswrapper module to the list that run at boottime, else you'll have to run the last command again every time you restart, use the following to do that:
```
sudo -s
echo ndiswrapper >> /etc/modules
exit
```

Lastly a bit of a forum hint: if you want to post alot of terminal output (ie error messages), it's better to enclose it in CODE tags rather than QUOTE tags, that way it takes up alot less thread real-estate. Plus it makes it easier for us since the reason for all the errors and warnings was contained in the first couple of lines! :)

A huge thanks  jw5801!

I copied you code exactly:

```
rich@Rich-Linux:~$ linux-headers-`uname -r`
bash: linux-headers-2.6.20-16-generic: command not found
rich@Rich-Linux:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rich@Rich-Linux:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rich@Rich-Linux:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rich@Rich-Linux:~$ cd /ndiswrapper-source-directory
bash: cd: /ndiswrapper-source-directory: No such file or directory
rich@Rich-Linux:~$ cd /ndiswrapper-1.47
bash: cd: /ndiswrapper-1.47: No such file or directory
rich@Rich-Linux:~$ z
bash: z: command not found
rich@Rich-Linux:~$ \
> cd
rich@Rich-Linux:~$ cd desktop
bash: cd: desktop: No such file or directory
rich@Rich-Linux:~$ cd Desktop
rich@Rich-Linux:~/Desktop$ cd ndiswrapper-1.47rich@Rich-Linux:~/Desktop/ndiswrapper-1.47$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /usr/sbin/ndiswrapper-buginfo
removing /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
removing /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
rich@Rich-Linux:~/Desktop/ndiswrapper-1.47$ sudo make
make -C driver
make[1]: Entering directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/rich/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/rich/Desktop/ndiswrapper-1.47/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/utils'
rich@Rich-Linux:~/Desktop/ndiswrapper-1.47$ sudo make install
make -C driver install
make[1]: Entering directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/rich/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
/sbin/depmod -a 2.6.20-16-generic -b /
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/driver'
make -C utils install
make[1]: Entering directory `/home/rich/Desktop/ndiswrapper-1.47/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/rich/Desktop/ndiswrapper-1.47/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
rich@Rich-Linux:~/Desktop/ndiswrapper-1.47$ cd /home/rich/Desktop/WMP54GS_20050406
rich@Rich-Linux:~/Desktop/WMP54GS_20050406$ driversbash: drivers: command not found
rich@Rich-Linux:~/Desktop/WMP54GS_20050406$ cd drivers
bash: cd: drivers: No such file or directory
rich@Rich-Linux:~/Desktop/WMP54GS_20050406$ cd Drivers
rich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ sudo ndiswrapper -i WMP54GS.inf
driver wmp54gs is already installed
rich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ sudo ndiswrapper -l
wmp54gs : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
rich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ sudo modprobe ndiswrapper
rich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ sudo modprobe ndiswrapper
rich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ \
> sudo modprobe ndiswrapper
rich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ \
> xcd
bash: xcd: command not found
rich@Rich-Linux:~/Desktop/WMP54GS_20050406/Drivers$ cd
rich@Rich-Linux:~$ sudo modprobe ndiswrapper
```

Everything seems to have gone fine except I dont know how to scan for a wireless signal. In windows I normally press 'scan for available connections' and my connection is found. I cant find any indication that my wifi card is installed so i can tweak any settings.

The linux platform and community backing seems great, i really like the concept and think i will enjoy learning about it all :)

Again, any help appricated.

Thanks

---

### Post by dca on 2007-09-07
I think you can click on the two monitor looking dealies in your tray and it should give an indication of what wireless APs are out there....

---

### Post by ayenack on 2007-09-07
Have a look at [this]("http://ohioloco.ubuntuforums.org/showthread.php?t=405990").

LOL
> [I]jw5801
No idea! But he had an issue compiling a program from source so we may as well teach him how to do that while he's here![/I]

PS. And also welcome to Ubuntu Richard. Can be a steep learning curve at times but well worth it in the final outcome.

---

### Post by P235 on 2007-09-07
This is how you scan for other networks.

sudo iwlist wlan0 scan

You should check out the threads I linked to.

---

### Post by SpiritIsReality on 2007-09-07
howdy

thanks all

trails

---

### Post by rtr86 on 2007-09-07
> **P235 said:**
> This is how you scan for other networks.

sudo iwlist wlan0 scan

You should check out the threads I linked to.


Thanks for reply,

This is what I get:

```
rich@Rich-Linux:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

```

---

### Post by ayenack on 2007-09-07
Do this instead

iwlist accesspoints

No need for sudo on this.:wink:

If you want to know what AP's are available do this.

iwlist scanning

If you want a list of the iwlist commands type iwlist interminal. Can you post the results of the two scans need to see if your card is up and running. If it is we'll get about setting up for your network.

---

### Post by rtr86 on 2007-09-07
> **ayenack said:**
> Do this instead

iwlist accesspoints

No need for sudo on this.:wink:

If you want to know what AP's are available do this.

iwlist scanning

If you want a list of the iwlist commands type iwlist interminal. Can you post the results of the two scans need to see if your card is up and running. If it is we'll get about setting up for your network.

Thanks for reply :)

Still having no luck; 
```
rich@Rich-Linux:~$ iwlist accesspoints
lo        Interface doesn't have a list of Peers/Access-Points

eth1      Interface doesn't have a list of Peers/Access-Points

eth0      Interface doesn't have a list of Peers/Access-Points

rich@Rich-Linux:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      No scan results
rich@Rich-Linux:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
rich@Rich-Linux:~$ 

```

Its strange, I would of thought after installing driver (which is appears to have done correctly: see log on previous page) I thought I woould of had some form of popup with a 'network' found message, i have not seen anything. Looking in the network manager app i cant even see anything related to the LINKSYS WMP54GS Card.

Really dont know what else todo.
Thanks for all help.

---

### Post by ayenack on 2007-09-07
This seems like a very good[ howto]("http://dossy.org/archives/000110.html") for your setup check it out.

So it seems that your wireless card is being reported as eth0 or eth1. Which isn't uncommon. I think you should check out these post also if you haven't already.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

For some in depth info on your card. It's a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) PCI card by the way.

The results of iwlist scanning should look something like this btw.

ayenack@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:FC:4D:14
                    ESSID:"ARANET"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:148 Mb/s

But with more Networks. Check out the threads above to try to get the card working. Also might be worth putting a post in Networking & Wireless on these forums.

good luck. ayenack. Let me know how it goes.

---

### Post by jw5801 on 2007-09-07
> A huge thanks  jw5801!

I copied your code exactly: 
...

Excellent. Well you notice how it told you your driver was already installed? That means you had been successful already the last time you tried! Just to be on the safe side I'd probably remove the driver you installed last time and reinstall it.
```
cd ~/Desktop/WMP54GS_20050406/Drivers
sudo rmmod ndiswrapper
sudo ndiswrapper -e WMP54GS
sudo ndiswrapper -i WMP54GS.inf
```

Now at this point, noticing that you're using a bcm43xx style card, you'll probably have to blacklist the broken and pretty much useless native driver that is included with the kernel, to do this do the following:
```
sudo -s
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
exit
```
You will need to reboot now!

When you come back online: all that's left to do is run ```
sudo modprobe ndiswrapper
```

And you should be up and running!

Now if you can't get your driver working yourself then I'd use the [script that someone linked to](http://ohioloco.ubuntuforums.org/showthread.php?t=405990), but it's always nice to know you can do stuff yourself and understand what's going on, it also makes it easier if something doesn't work! Note that to use the script above you will possibly have to undo some of the steps that I've given, so if you're unsure how to do that then let me know! Or if you're unsure what any of the commands I've listed do then feel free to ask and I shall explain!

**EDIT:** [This](http://dossy.org/archives/000110.html) howto that ayenack posted looks to be quite good! But he is using a VERY old version of ndiswrapper, so I'd just skip all the steps about installing ndiswrapper if you have a look there.

Also I just noticed that he's using a different driver, so if we can't get it up and running with your newer driver then we'll go back to the one he has working, although it appears to be a very old howto.

---

### Post by ayenack on 2007-09-07
I think but am not sure that the newer drivers cause some problems and it's better to use the older version.... have even heard that it's an idea to use 98 drivers. Why.... beats me but I believe this to be true. Other than that check out [this]("http://ohioloco.ubuntuforums.org/showthread.php?t=405990") post that I listed earlier.

ayenack.

---

### Post by jw5801 on 2007-09-07
I don't like the look of scripts like that, looks far too much like automatix to me. So while it may work, it may also stuff up and be incredibly hard to debug!

Give the new driver a shot, the main thing that would have been stopping it working before would have been the kernel trying to use the bcm43xx driver, so once you blacklist that you should have a better chance. If you still don't have any luck then try the older driver listed in the how to mentioned by ayenack earlier.

As always if you find anything you can't manage or don't understand post here and we'll do our best to help!

---

### Post by ayenack on 2007-09-07
> [I]Posted by jw5801
I don't like the look of scripts like that, looks far too much like automatix to me. So while it may work, it may also stuff up and be incredibly hard to debug![/I]

That's certainly a possibility.

I have a feeling that he may have given up the ghost. No post for awhile. Ah well.

---

### Post by rtr86 on 2007-09-08
Guys, it works :) i'm so pleased &#8211; Another HUGE thanks to all you very kind posters :) Really is appreciated.  I am now posting this to you ........ wirelessly. 

ayenack> Thanks for links :), i have noted down all links you guys have recommended and will be working my way through them today. 

I think the problem could have been ndiswrapper was using an alternative driver for some reason. I'll do some research into why that was :)

Also, i never realised you could use really old drivers, will remember i for future use.
The driver I am currently using for the LINKSYS WMP54GS is the one recommended by ndiswrapper:

> Card: Linksys WMP54GS Wireless-G PCI Adapter with Speedbooster
Chipset: Broadcom Corporation BCM94306 802.11g (rev 03)
pciid: 14e4:4320
Driver: Linksys [ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe](ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe) (new version)
Other: Ndiswrapper 0.11 and 0.12. Works fine with 64-bit WEP key and WPA supplicant (Fedora core-2, Kernel 2.6.8 and 2.6.9). Use WMP54GS.inf


This is what islist looks like now: 

```
rich@Rich-Linux:~$ iwlist scanning

lo        Interface doesn't support scanning.



eth1      Interface doesn't support scanning.



eth0      Scan completed :

          Cell 01 - Address: 00:16:B6:DA:60:68

                    ESSID:"dd-wrt"

                    Protocol:IEEE 802.11g

                    Mode:Managed

                    Frequency:2.437 GHz (Channel 6)

                    Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s

                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:atim=0

```

jw5801> Can't thank you enough :) Copied your code again which resulted in the wifi card working  straight away from reset.  It seems like the problem was what you said, the 'alterntive' driver was causing the problems.

I can now move the linux pc back in another room and do some more learning, as I had to move my main PC and connect it directly to net :) 

Also guys, are there any kind of 'registry' scanners, I know there is not a 'registry' like windows but is there anything that scans for errors? When I first installed ubunto i was putting lots of different codes in terminal trying to get wifi working &#8211; I'm a bit worried I may have caused some problems that might crop up in future.

Regards,

Richard

---

### Post by jw5801 on 2007-09-08
Yeah you're absolutely correct, when both the ndiswrapper module and the bcm43x modules are running the bcm43xx interferes with the operation of ndiswrapper so your driver won't function properly. It's not ndiswrapper using an alternate driver, but bcm43xx is a native attempt at a driver for broadcom chipsets, which in most cases will not work at all! Ndiswrapper is another module that poses as a 'native' driver by 'translating' (a better word doesn't immediately spring to mind but I'm sure there is one) the windows equivalent driver.

As for a clean up program, I'm not all that sure. It's unlikely you could have done all that much unless you installed and uninstalled a bunch of programs. Even then, Linux is completely unlike Windows, unless it tells you there was an error when you remove a program there isn't going to be any trace of it left behind! The only things that will remain by default are any settings that it may have saved to your home directory, and these won't interfere with anything other than taking up a bit of diskspace! The only thing you could have done that might have an impact on anything is added an extra driver entry to ndiswrapper, but ```
sudo ndiswrapper -l
```will tell you if you've done that. You can't really leave anything behind in Linux that will slow your system down, so it's not really worth the worry. Just like there's no need to regularly defragment your drive while you're using Linux. That being said I'm sure there's an app out there somewhere to have a look at your directories and clean them up, but I have no idea where!

---

### Post by rtr86 on 2007-09-08
> **jw5801 said:**
> Yeah you're absolutely correct, when both the ndiswrapper module and the bcm43x modules are running the bcm43xx interferes with the operation of ndiswrapper so your driver won't function properly. It's not ndiswrapper using an alternate driver, but bcm43xx is a native attempt at a driver for broadcom chipsets, which in most cases will not work at all! Ndiswrapper is another module that poses as a 'native' driver by 'translating' (a better word doesn't immediately spring to mind but I'm sure there is one) the windows equivalent driver.

As for a clean up program, I'm not all that sure. It's unlikely you could have done all that much unless you installed and uninstalled a bunch of programs. Even then, Linux is completely unlike Windows, unless it tells you there was an error when you remove a program there isn't going to be any trace of it left behind! The only things that will remain by default are any settings that it may have saved to your home directory, and these won't interfere with anything other than taking up a bit of diskspace! The only thing you could have done that might have an impact on anything is added an extra driver entry to ndiswrapper, but ```
sudo ndiswrapper -l
```will tell you if you've done that. You can't really leave anything behind in Linux that will slow your system down, so it's not really worth the worry. Just like there's no need to regularly defragment your drive while you're using Linux. That being said I'm sure there's an app out there somewhere to have a look at your directories and clean them up, but I have no idea where!

Thanks again, its all becoming a lot clearer now :)

When I moved the computer to spare room and booted up I had the same problem with wireless not showing, i guessed it was linux not knowing it should of loaded ndiswrapper, so I typed a code you listed earlier:

```
sudo ndiswrapper -l

```

In terminal and now everything is ok again :)

Im guessing I want to run that on bootup all the time though, as i would need to keep typing it in terminal. Am I right in saying I should load boot moduls by:

```
sudo gedit /etc/modules

``` 

And listing it at bottom? At the moment my startup list looks like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
```


Again, big thanks!

**EDIT:** By the way, my 'sudo ndiswrapper -l' looks like this:

```
rich@Rich-Linux:~$ sudo gedit /etc/modules
rich@Rich-Linux:~$ sudo ndiswrapper -l
wmp54gs : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

```

Even though it says its using a alternate driver I'm guessing thats right as we have told Linux to blacklist that one?

---

### Post by jw5801 on 2007-09-08
> **rtr86 said:**
> Thanks again, its all becoming a lot clearer now :)
Im guessing I want to run that on bootup all the time though, as i would need to keep typing it in terminal. Am I right in saying I should load boot moduls by:

```
sudo gedit /etc/modules

``` 

And listing it at bottom? At the moment my startup list looks like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
```

Yup that's exactly right. Although it's best to use "gksudo" rather than regular "sudo" to open a graphical app. gksudo is the graphical equivalent, most times you can use them interchangeably but once every now and then it'll muddle up the permissions on a file which can be bad.

> 
Again, big thanks!

**EDIT:** By the way, my 'sudo ndiswrapper -l' looks like this:

```
rich@Rich-Linux:~$ sudo gedit /etc/modules
rich@Rich-Linux:~$ sudo ndiswrapper -l
wmp54gs : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

```

Even though it says its using a alternate driver I'm guessing thats right as we have told Linux to blacklist that one?

Yup! That's why we blacklisted it, so linux knows it doesn't work so it shouldn't use it. 

Once you add ndiswrapper to the modules list then you'll probably never need to think about this again! Keep the source code and drivers on hand though, if your kernel headers or the kernel itself ever get updated then you'll need to recompile ndiswrapper. But that's pretty easy since you know how now! Basically if you ever find it not working after an update, best bet is to remove the driver, then remove the module, then run "sudo make uninstall, sudo make, sudo make install" again, then readd the driver, then readd the module, and that will get you back up and running. Kernel updates don't come along all that often so you don't really need to worry about it.

And as always if you encounter any issues just post here and everyone will do what they can to help! Enjoy Linux!

---

### Post by rtr86 on 2007-09-08
[QUOTE=jw5801]



Yup! That's why we blacklisted it, so linux knows it doesn't work so it shouldn't use it. 

Once you add ndiswrapper to the modules list then you'll probably never need to think about this again! Keep the source code and drivers on hand though, if your kernel headers or the kernel itself ever get updated then you'll need to recompile ndiswrapper. But that's pretty easy since you know how now! Basically if you ever find it not working after an update, best bet is to remove the driver, then remove the module, then run "sudo make uninstall, sudo make, sudo make install" again, then readd the driver, then readd the module, and that will get you back up and running. Kernel updates don't come along all that often so you don't really need to worry about it.

And as always if you encounter any issues just post here and everyone will do what they can to help! Enjoy Linux![/QUOTE]

Hi jw5801,

Ive made a note of the installation commands for installing my wifi card if I need to do so again in future,  :)

I quoted a code wrong earlier too. To get wifi working on a reset I need to input 'sudo modprobe ndiswrapper' rather then  'sudo ndiswrapper -l', I copied it wrong sorry.

At the moment my startup list looks like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
gksudo modprobe ndiswrapper
```

But on a reboot the network is not found, I need to input 'sudo modprobe ndiswrapper' manually in console for it too work. I am also asked for my password; do you think the bootlist is not being loaded correctly because it needs me to enter password (like it does in terminal)?

Really do appreciate your help jw5801 (and other contributors), would not be online now without you.

Regards,

RIchard

---

### Post by jw5801 on 2007-09-08
All it needs to be is:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper
```
"ndiswrapper" is a kernel module which needs to be loaded at boot time. "sudo modprobe ndiswrapper" is a command used to manually load the kernel module at a later time.

Before I meant that you should use:
```
gksudo gedit /etc/modules
```
rather than using regular sudo. As gedit is a graphical application that you want to run as root, you should use the "Graphical Sudo." Running a text editor is about the only time you'll need to run an application from the terminal with root permissions, almost all apps shouldn't be run with root permissions. The only ones I've ever needed to use it for are, gedit, wireshark and gparted. The first is a text editor to edit important files, the second is a network packet analyser (which needs root permissions so it can read directly from the network card I guess), and the last is a partition editor, which is of course going to need root permissions. There's a thread around about the difference between sudo and gksudo and where to use each, hang on and I'll find it.

EDIT: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

And just for your future reference I thought I'd give a run down of the commands needed to recompile ndiswrapper, and what they all do:
```
sudo ndiswrapper -e wmp54gs #removes the driver
sudo rmmod ndiswrapper #removes the module
cd /*ndiswrapper-source-directory* #cd=change directory, replace italics with the correct location
sudo make uninstall #removes the old kernel module
sudo make uninstall #it's best to run it a couple of times as the makefile suggests that we should
sudo make uninstall #one more for good measure!
sudo make #compiles the installer
sudo make install #recompiles the module for the new kernel (or new linux-headers)
cd /*driver-directory* #once again replace the italics with whereever your .inf and .sys files are
ls | grep WMP54GS #verify you're in the right directory (saves the confusion that might happen if you're not)
sudo ndiswrapper -i wmp54gs.inf #reinstall the driver
sudo modprobe ndiswrapper #insert the recompiled module into the kernel
```
You won't need to blacklist the bcm43xx module again, nor will you need to reedit /etc/modules, so once the above is done you should be back up and running! If you're curious, the command:
```
ls | grep WMP54GS
```
is actually 2 commands in one,
"ls" lists files in directory 
"|" tells the shell to send the output of previous command to input of the next
"grep" filters a text output and only displays lines containing the specified string.
Therefore the command as a whole should show you both the .inf and .sys files for your driver.

It's also good to note that WMP54GS is completely different to wmp54gs in a linux environment so if you don't see it then try the alternate case... or just use "ls" since there probably aren't that many files in the directory anyway, I just like being fancy! It's a good command to know for use in other situations anyway though.

Well that concludes my little speech about the terminal and ndiswrapper for today! Glad I've been able to help and hope you enjoy Linux and Ubuntu as much as I do!

---

### Post by rtr86 on 2007-09-08
jw5801> Everything now works perfect, no problems at all. Also getting to understand the commands a bit more also now.:)

 Thanks loads for the recompile ndiswrapper walk through, I have saved a copy for future reference, I'm guessing I will need to follow that exact procedure when I next update the headers also? (I think you mentioned that header updates are rare but required and that associated modules need recompiling?

Hopefully I will be able to return a favor in the future for you.  I doubt it will be about Linux though, your knowledge on the subject seems immense :)

---

### Post by jw5801 on 2007-09-08
> **rtr86 said:**
> jw5801> Everything now works perfect, no problems at all. Also getting to understand the commands a bit more also now.:)

 Thanks loads for the recompile ndiswrapper walk through, I have saved a copy for future reference, I'm guessing I will need to follow that exact procedure when I next update the headers also? (I think you mentioned that header updates are rare but required and that associated modules need recompiling?

Hopefully I will be able to return a favor in the future for you. I doubt it will be about Linux though, your knowledge on the subject seems immense :)

Yup, you're absolutely correct! Only modules you've compiled yourself will need to be updated, so this will probably be the only thing you'll need to recompile. Other apps that you've compiled from source won't need to be recompiled unless they also involve kernel modules, so if they interface right down to the hardware level (ie. a video or audio driver). However anything installed from the repositories will be updated by the good folks who maintain those repositories, so you don't need to worry about those.

Always glad to be of help, that's what this community is all about! :popcorn:

---

