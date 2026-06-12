---
title: "NDISWRAPPER install errors...help!"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by chlorinekid on 2006-11-26
im trying to install ndiswrapper on ubuntu 6.10 but i keep getting the erros below when i try to 'make' and 'make install' the file...

for some reason it was working yesterday but ive since formatted the laptop with a fresh install of ubuntu.

can someone explain the error code??? what do i have to do to fix this?? it looks like it cant find the files it wants...

```
dave@dave-laptop:~$ cd /home/dave/programs/ndiswrapper-1.28
dave@dave-laptop:~/programs/ndiswrapper-1.28$ sudo make
Password:
make -C driver
make[1]: Entering directory `/home/dave/programs/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/dave/programs/ndiswrapper-1.28/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/dave/programs/ndiswrapper-1.28/driver'
make -C utils
make[1]: Entering directory `/home/dave/programs/ndiswrapper-1.28/utils'
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
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:219: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:219: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:221: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:223: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:224: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:226: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:232: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:234: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:234: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:234: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:252: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:254: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:262: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:264: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:270: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:270: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:274: warning: implicit declaration of function ‘memset’
loadndisdriver.c:274: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:275: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:283: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:283: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:285: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:290: warning: implicit declaration of function ‘stat’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:291: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:292: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:308: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:316: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:316: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:317: error: dereferencing pointer to incomplete type
loadndisdriver.c:320: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:321: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:324: error: dereferencing pointer to incomplete type
loadndisdriver.c:285: warning: unused variable ‘statbuf’
loadndisdriver.c:347: error: expected expression before ‘struct’
loadndisdriver.c:349: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:351: warning: implicit declaration of function ‘free’
loadndisdriver.c:358: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:360: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:360: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:371: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:374: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:377: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:378: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:380: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:380: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:403: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:371: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:415: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:415: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:420: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:422: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:425: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:430: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:431: error: dereferencing pointer to incomplete type
loadndisdriver.c:432: error: dereferencing pointer to incomplete type
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:444: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:461: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:461: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:469: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:469: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:470: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:470: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:485: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:486: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:486: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:486: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:488: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:493: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:509: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:509: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:513: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:515: warning: implicit declaration of function ‘printf’
loadndisdriver.c:515: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:525: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:540: warning: implicit declaration of function ‘atof’
loadndisdriver.c:547: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:554: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:588: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/dave/programs/ndiswrapper-1.28/utils'
make: *** [all] Error 2
dave@dave-laptop:~/programs/ndiswrapper-1.28$
```

---

### Post by wieman01 on 2006-11-26
Just one thing... You know that you find "ndiswrapper" in the repositories, right? Why would you want to compile from source? Simply install it via Synaptic.

---

### Post by chlorinekid on 2006-11-26
yes, ive just figured it out and got it installed thankfully. im pretty sure ive got the driver installed now but i cant see any wireless connections in the admin > networking menu...

just to summerize, this is what ive typed:

```
sudo ndiswrapper -i NetW33.inf
```

which seems to install the driver as i get:

"driver installed, hardware present"

then, i believe i have to type:

```
sudo modprobe ndiswrapper
```

..which ive done

so what next? ive re-started the computer and unplugged the ethernet cable that i was using but its still not listed in admin > networking and "iwconfig" returns:

```
dave@dave-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

i have to type "dhclient" to the eth0 working...is there a similar command for the wireless?

---

### Post by wieman01 on 2006-11-26
You need to perform all these steps & also need to blacklist the native wireless driver... 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

What chipset have you got?

---

### Post by chlorinekid on 2006-11-26
i think its the [Intel] PRO/Wireless 3945ABG...

---

### Post by chlorinekid on 2006-11-26
ooh no its a Winbond w89c33 mPCI, i dont think its listed on the ndiswrapper website though :/

---

### Post by wieman01 on 2006-11-26
Please post the contents of these two files:
> cat /etc/modprobe.d/ndiswrapper
> cat /etc/networking/interfaces
And do a scan (post the results please):
> iwlist scan
And check for your device:
> lspci

---

### Post by chlorinekid on 2006-11-26
cat /etc/modprobe.d/ndiswrapper:

> alias wlan0 ndiswrapper


cat /etc/networking/interfaces:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iwlist scan:

> 
lo   interface dosnt support scanning

eth0  interface dosnt support scanning

sit0   interface dosnt support scanning


lspci:

> dave@dave-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:02.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
01:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Ethernet controller: Winbond Electronics Corp Unknown device 0033
dave@dave-laptop:~$ 



does that tell you anything?? i notice wlan0 is listed a few time... ive not seen that anywhere before

is that last line in the last quote the wlan?? winbond is the make...

---

### Post by wieman01 on 2006-11-26
"wlan0" stands for "ndiswrapper" & your wireless device. Can you also post this please:
> lshw
And have you blacklisted the native Linux driver?

---

