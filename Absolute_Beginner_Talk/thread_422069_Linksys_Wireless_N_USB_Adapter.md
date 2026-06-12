---
title: "Linksys Wireless N USB Adapter"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by mciarlo on 2007-04-24
Hello, 

I am a complete Linux noob, but was very interested in trying it out. I have been using Windows for years and decided to give it a go.

After a painless install (was a bit confusing to get the partition setup, but I found a great install guide), I am trying to connect to the internet.  I am using Ubuntu 7.04 for 32-bit computers. 

I downloaded ndiswrapper-1.42.tar.gz and its sitting on my ubuntu desktop. I have no idea how to install it. I tried using terminal and following the guide on the ndiswrapper wiki, but was unsuccessful. ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation))

I keep getting something like 'could not find folder or directory. stop.' 

Any help on getting my internet up and running would be very much appreciated!

---

### Post by tyner100 on 2007-04-24
Im having the same problem, and ive gotten some help i havent understood here is a link to the thread

[http://ubuntuforums.org/showthread.php?p=2528197#post2528197](http://ubuntuforums.org/showthread.php?p=2528197#post2528197)

---

### Post by mciarlo on 2007-04-24
I was just looking at that. Unfortunately, I don't understand what you did to get it installed or whcih files are necessary to download and which aren't.

---

### Post by tyner100 on 2007-04-24
Seems like we are in the same boat, with no bananas.


:( 


i like bananas.



SOME ONE PLEASE HELP US!

WAH WAH WAH :(

---

### Post by bobplano on 2007-04-24
to install ndiswrapper from source (the tar.gz) you need to extract and compile it.  if you want to extract it with commands i think the command is
```
 tar xvfz ndiswrapper-1.4.2.tar.gz
```
to compile it you need make, and to get make you need to go to [packages.ubuntu.com]("packages.ubuntu.com") (if your ubuntu doesn't have an internet connection and get cpp, gcc, build-essential, and linux-headers(depends on your kernel). if you do have internet for ubuntu you can run 
```
cpp gcc build-essential linux-headers-$(uname -r)
```
then you can run make. go to the directory where you extracted ndiswrapper to and run 
```
make
make install
```

then you can run ```
sudo ndiswrapper -i */path/to/driver driver name*
```

to check and see if it's fine run 
```
ndiswrapper -l
``` 
you might need to install system files which you can get off the cd and for that it should be something like
```
 sudo cp *system file* /etc/ndiswrapper/*name of adapter*
```

to get ndiswrapper to start everytime you boot your computer run
```
sudo ndiswrapper -m
```
i think you might also need to run this command before sudo ndiswrapper -m
```
 sudo modprobe ndiswrapper
```
if any part of this comes up with errors poet them here

---

### Post by mciarlo on 2007-04-24
When running the make command it appears to copy everything correctly, but:

michael@michael-desktop:~/ndiswrapper-1.42$ make
make -C driver
make[1]: Entering directory `/home/michael/ndiswrapper-1.42/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/michael/ndiswrapper-1.42/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/michael/ndiswrapper-1.42/driver/built-in.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/crt.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/hal.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/iw_ndis.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/loader.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/ndis.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/ntoskernel.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/ntoskernel_io.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/pe_linker.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/pnp.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/proc.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/rtl.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/wrapmem.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/wrapndis.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/wrapper.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/usb.o
  CC [M]  /home/michael/ndiswrapper-1.42/driver/divdi3.o
  LD [M]  /home/michael/ndiswrapper-1.42/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/michael/ndiswrapper-1.42/driver/ndiswrapper.mod.o
  LD [M]  /home/michael/ndiswrapper-1.42/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/michael/ndiswrapper-1.42/driver'
make -C utils
make[1]: Entering directory `/home/michael/ndiswrapper-1.42/utils'
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
loadndisdriver.c:179: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:179: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:206: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:218: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:218: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:222: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:223: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:225: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:233: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:250: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:250: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:252: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:256: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:256: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:258: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:260: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:268: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:272: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:281: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:319: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:345: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:347: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:349: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:356: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:356: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:356: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:358: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:358: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:368: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:371: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:371: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:375: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:368: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:420: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:420: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:424: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:424: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:427: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:428: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:430: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:448: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:465: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:465: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:473: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:473: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:474: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:474: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:484: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:484: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:489: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:490: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:490: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:490: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:491: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:496: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:512: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:512: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:512: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:512: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:512: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:514: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:516: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:518: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:518: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:528: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:543: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:550: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:557: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:591: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/michael/ndiswrapper-1.42/utils'
make: *** [all] Error 2
michael@michael-desktop:~/ndiswrapper-1.42$ 



Not quite there. I do have cpp, gcc, libc6, build-essentials, linux-headers etc installed. I want my internet!

---

### Post by bobplano on 2007-04-25
did you get the right linux headers? there are quite a few. run uname -r in the terminal to get your kernel, but i don't know what type of headers you need

---

