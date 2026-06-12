---
title: "problem compiling wireless driver"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by pavelo on 2007-12-06
hi everyone,
i've just installed ubuntu 7.10 on my toshiba equium p200. everything works fine exept for the wireless card. it's an atheros ar5006eg.
ubuntu seems to recognize the wireless network and tells me that those are restricted drivers.

I see the card with lspci:
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
I see the modules with lsmod:
ath_pci                98336  0 
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci


but i can't see it with the network admin gui (i see only the wired one)
also iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.

so I tried to compile the madwifi driver, but when I do make:

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/madwifi-ng-r3005-20071205 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  HOSTCC  /root/madwifi-ng-r3005-20071205/ath_hal/uudecode
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c: In function 'uudecode_usage':
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c: At top level:
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c: In function 'main':
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:121: error: for each function it appears in.)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/root/madwifi-ng-r3005-20071205/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/root/madwifi-ng-r3005-20071205/ath_hal/uudecode] Error 1
make[2]: *** [/root/madwifi-ng-r3005-20071205/ath_hal] Error 2
make[1]: *** [_module_/root/madwifi-ng-r3005-20071205] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

help pls!
thanks!

---

### Post by CaptainInsaneO on 2007-12-06
Try
```
sudo apt-get install build-essential
```

and then do make install again.

---

### Post by pavelo on 2007-12-06
I tried to install build-essential, but I haven't a internet connection on that machine. so I downloaded the package build-essential_11.1_i386.deb.
but when i do:

apt-get install build-essential_11.1_i386.deb
Reading Packages lsits... Done
Building dependency tree
Reading state information... Done
E: couldn't find package build-essential_11.1_i386.deb

any help

---

### Post by CaptainInsaneO on 2007-12-06
Just double click the deb file. It should install automatically.

---

### Post by pavelo on 2007-12-06
driver compiled!
the problem was on the file permissions!
now i've a problem configuring the card with wlanconfig.
i'll ask some help in the madwifi forum!
thank you very much!

---

### Post by CaptainInsaneO on 2007-12-06
Glad I could help.

---

