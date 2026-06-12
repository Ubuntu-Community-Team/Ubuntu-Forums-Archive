---
title: "Live CD &amp; Laptop Wireless problems"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Auraya on 2007-04-16
I thought I would try the live CD on my laptop and have read as many threads relating to wireless problems on here as I can but none seem to relate. I have tried a couple of different ways to solve it just from searching online but none seem to work. Obviously I don't want to install Ubuntu if I'm not going to be able to use my wireless. One of the things which I think may be causing the problem is my laptop has a button which enables my wireless to switch on and when I press it while using the CD nothing happens.

sudo lshw -C network gives me this:

*-network:0
  description: Ethernet interface
  product: RTL - 8139/8139C/8139C+
  vendor: Realtek Semiconductor Co., Ltd.
  physical id: 2
  bus info: pci@02:02.0
  logical name: eth0
  version: 10
  serial: 00:19:21:52:49:c9
  size: 10MB/s
  capacity: 100MB/s
  width: 32 bits
  clock: 33MHz
  capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1
00bt 100bt-fd autonegociation=on broadcast=yes driver=8139too driververs
ion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
  resources: ioport:e800-e8ff iomemory:febffcff irq:201
 *-network:1 UNCLAIMED
  description: Ethernet controller
  product: 88w8335 [libertas] 802.11b/g Wireless
  vendor: Marvell Technology Group Ltd.
  physical id: 4
  bus info: pci@02:04.0
  version: 43
  width: 32 bits
  clock: 66MHz
  capabilities: bus_master cap_list
  resources: iomemory:febe0000-febeffff iomemory:febd0000-febdffff irq:7

(I hope I typed that all in right! Couldn't copy and paste due to using the internet on desktop)

Hopefully someone can help, if I need to give anymore info just ask!

---

### Post by lamalex on 2007-04-16
could you give the output of lspci? don't trust the livecd for wireless, often wireless requires restarts and some setup to get working because companies don't really like Linux :(

---

### Post by Auraya on 2007-04-16
lspci output:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configeration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 43)

---

### Post by Auraya on 2007-04-16
Any other info needed?

---

### Post by Auraya on 2007-04-16
I decided to go for it and take your advice about not trusting the live CD. So I have now installed Ubuntu, Im having the same problem with the button which is supposed to switch on my wireless which Im assuming could be down to a driver problem or lack thereof?

---

### Post by n3tfury on 2007-04-16
i found this information for you:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by Auraya on 2007-04-16
Thanks n3tfury Im working my way through it now :D Will let you know how it goes!

---

### Post by Auraya on 2007-04-16
I tried two different versions of ndiswrapper - both the one used by the author and the newest version and with both I get an error when I get to the "user@ubuntu:~/ndiswrapper-1.29$ make", it starts off fine and then errors halfway through leaving the laptop completely frozen

---

### Post by Auraya on 2007-04-16
I found [https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983"]this]("https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983") about a bug in edgy and tried using ndiswrapper 1.8 and Im getting an error in the same place.

---

### Post by n3tfury on 2007-04-16
uh, that's odd... i had posted after you said you got that error in your previous post saying that that error isn't something i'm familiar with and that someone else will hopefully chime in and give a helping hand.  it's a good community here, so i'm sure it'll get sorted.

---

### Post by Auraya on 2007-04-16
I saw something in another post (I think it was just above mine) about edgy having problems with wireless cards and feisty being better so Im downloading feisty as we speak!

---

### Post by nautilus on 2007-04-16
in any case, ndiswrapper will need to work, so it might be jumping the gun to throw on a new distro version.

i noticed you were installing ndiswrapper 1.29, but ndiswrapper is at 1.41, and at least 1.41 is working for me.

it may be an easier compile, at least, and 1.41 supports the newer, crazy things, such as wifi cards on a PCI-E bus, which yours is.

but now that i think about it, 2.6.20 is the earliest kernel supporting wifi on PCI-E anyway, and 2.6.20 only comes with feisty if i remember correctly ... so...

...forget what i said about jumping the gun, and grab a fresh copy of ndiswrapper while you're at it! :)

---

### Post by Auraya on 2007-04-16
I tried the newest version of ndiswrapper (1.42) then I tried 1.29 (which was the one used in the guide I was recommended on page 1, then I tried 1.18, then I tried 1.8 which was recommended on a guide about problems with edgy and wireless cards! None of them worked, they all errored when I tried to "make", it starts off fine and errors halfway through

---

### Post by nautilus on 2007-04-16
could be a simple thing, any chance you could type out the error, or copy/paste it?

on second thought, don't sweat it, let's just see how feisty does.

---

### Post by Auraya on 2007-04-16
Here is the error

auraya@Auraya:~/ndiswrapper-1.42$ make
make -C driver
make[1]: Entering directory `/home/auraya/ndiswrapper-1.42/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/auraya/ndiswrapper-1.42/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /home/auraya/ndiswrapper-1.42/driver/built-in.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/crt.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/hal.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/iw_ndis.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/loader.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/ndis.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/ntoskernel.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/ntoskernel_io.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/pe_linker.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/pnp.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/proc.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/rtl.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/wrapmem.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/wrapndis.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/wrapper.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/usb.o
  CC [M]  /home/auraya/ndiswrapper-1.42/driver/divdi3.o
  LD [M]  /home/auraya/ndiswrapper-1.42/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/auraya/ndiswrapper-1.42/driver/ndiswrapper.mod.o
  LD [M]  /home/auraya/ndiswrapper-1.42/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/auraya/ndiswrapper-1.42/driver'
make -C utils
make[1]: Entering directory `/home/auraya/ndiswrapper-1.42/utils'
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
make[1]: Leaving directory `/home/auraya/ndiswrapper-1.42/utils'
make: *** [all] Error 2

---

### Post by Auraya on 2007-04-17
Installed Feisty and getting the same error.

---

### Post by stump138 on 2007-04-17
are you using aptitude to install ndiswrapper?

You should be able to get a clean install from

sudo aptitude update && sudo aptitude install ndiswrapper-utils-1.8

---

### Post by Auraya on 2007-04-17
Im on wired internet now but Im still having problems with the ndiswrapper, I entered both those commands and the first was fine, the second spits out a load of stuff but finishes saying:

> 0 packages upgraded, 0 newly installed, 0 to remove and 337 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

So does that mean it didnt install ndiswrapper-utils-1.8?

---

### Post by stump138 on 2007-04-17
you can also try it this way

sudo aptitude update && sudo aptitude install ndiswrapper-utils

If you try sudo aptitude install ndiswrapper
This will give you a list of packages including ndiswrapper



If ndiswrapper is already installed correctly (or you aren't sure) try typing 

ndiswrapper -v 

that should give you version information.  Once installed you can see if the drivers loaded properly by typing

ndiswrapper -l

---

### Post by seetho on 2007-04-17
The wireless network never worked for me when I used the Edgy Live CD.  I tried it on My IBM X31 and Acer 5672.  However when I installed Ubuntu on the harddrive using the Alternate CD wireless worked on both.  However Edgy out of the box does not work with WPA.  You need to install network-manager-gnome for that.

---

### Post by Auraya on 2007-04-17
Think Ive nearly got it, got ndiswrapper installed doing modprobe at the moment *crosses fingers & toes*

---

