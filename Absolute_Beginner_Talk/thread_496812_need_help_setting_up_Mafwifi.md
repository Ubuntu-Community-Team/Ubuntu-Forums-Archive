---
title: "need help setting up Mafwifi"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by i986 on 2007-07-09
I tried installing it from source using the "make" command, but I get a whole bunch of error messages....

```
isaac@onetwoeight:~/Desktop/madwifi-0.9.3/madwifi-0.9.3$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  HOSTCC  /home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c: At top level:
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c: In function 'main':
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode] Error 1
make[2]: *** [/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal] Error 2
make[1]: *** [_module_/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
isaac@onetwoeight:~/Desktop/madwifi-0.9.3/madwifi-0.9.3$
```

and I've checked with I don't remember what command, but the chip for my wifi is Atheros.

---

### Post by jskracht on 2007-07-09
I use an atheros card with the madwifi drivers that come with Ubuntu. 
I'm pretty sure your card should work without installing those drivers. 
If you really need them I suggest you download rpms and install them with something like kpackage.

Hope that helps

---

### Post by Paris Heng on 2007-07-12
Dear jskracht,

Are you sure you can use the Wifi card (atheros) without installing any of the Madwifi driver?

I am having the same problem like MR. i986. I am un-installing the Restricted-Module in the kernel. But it doen't help. Any idea to solve this problem?

---

### Post by Outrunner on 2007-07-12
These should come installed with your Ubuntu installation. What happens if you type

```
sudo modprobe ath_pci
```

---

### Post by Paris Heng on 2007-07-12
> **Outrunner said:**
> These should come installed with your Ubuntu installation. What happens if you type

```
sudo modprobe ath_pci
```
Dear sir, 

(1) What is** cd** **/usr/src**, i need to create it or i already in the system file?

(2) i un-istall the Restricted-Module in kernel already,

Restricted-Module:-

Currently the following modules are included:
  - **madwifi (Atheros)**
  - fglrx (ATI)
  - nvidia
  - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
  fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
  - ltmodem (Winmodem)

(3) You mean, when I insert the Atheroes based card inside the slot, the system will automatically install the Madwifi driver? ANyway i am using Ubuntu 7.04

(4) What different between Madwifi-ng and Madwifi, it is the same?

(5) I now in campus, later i go back and try *sudo modprobe ath_pci*, will let you know later.

Very glad that you can help.

---

### Post by Outrunner on 2007-07-12
Why did you uninstall the restricted-modules? They're supposed to be installed. After you install them again, type the command I gave you...

---

