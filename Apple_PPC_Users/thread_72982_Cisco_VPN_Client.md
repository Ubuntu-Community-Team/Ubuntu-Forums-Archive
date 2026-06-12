---
title: "Cisco VPN Client"
date: 2005-10-07
forum: Apple PPC Users
---

### Post by jgreenleaf on 2005-10-07
I am new to Linux and wanted to get my VPN working, I tried following these instructions, [http://www.ubuntuforums.org/showthread.php?t=21054&page=3&highlight=vpn](http://www.ubuntuforums.org/showthread.php?t=21054&page=3&highlight=vpn)
but I get this error, I am using kernal 2.6.10-5-powerpc. Here is the output of the attempted install

root@G4:/usr/src # tar xzvf vpnclient-linux.tar.gz
vpnclient/
vpnclient/Makefile
vpnclient/linuxcniapi.c
vpnclient/vpnclient
vpnclient/vpnclient.ini
vpnclient/libdriver.so
vpnclient/ipseclog
vpnclient/vpn_uninstall
vpnclient/linux_os.h
vpnclient/interceptor.c
vpnclient/MacConnect.pcf
vpnclient/IPSecDrvOS_linux.h
vpnclient/cisco_cert_mgr
vpnclient/driver_build.sh
vpnclient/unixcniapi.h
vpnclient/Cniapi.h
vpnclient/license.rtf
vpnclient/mtu.h
vpnclient/libvpnapi.so
vpnclient/cvpnd
vpnclient/license.txt
vpnclient/McMasterVPN.pcf
vpnclient/GenDefs.h
vpnclient/vpn_install
vpnclient/IPSecDrvOSFunctions.h
vpnclient/vpn_ioctl_linux.h
vpnclient/frag.c
vpnclient/linuxcniapi.h
vpnclient/vpnapi.h
vpnclient/config.h
vpnclient/sample.pcf
vpnclient/vpnclient_init
vpnclient/IPSecDrvOS_linux.c
vpnclient/frag.h
root@G4:/usr/src # cd vpnclient
root@G4:/usr/src/vpnclient # sudo sh vpn_install
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserve d.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/lin ux by default
For RedHat 7.x users these files are installed in /usr/src/lin ux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux -2.4.10.SuSE by default

Directory containing linux kernel source code []

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.10-5-powerpc/ CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "" will be used to build the module.

Is the above correct [y]

Making module
./driver_build.sh
Cisco Systems VPN Client Version BUILDVER_STRING
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserve d.

usage:
    ./driver_build.sh 'kernel_src_dir'

'kernel_src_dir' is the directory containing the linux kernel sour
ce

Failed to make module "cisco_ipsec.ko".
root@G4:/usr/src/vpnclient # ./vpn_install
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserve d.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/lin ux by default
For RedHat 7.x users these files are installed in /usr/src/lin ux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux -2.4.10.SuSE by default

Directory containing linux kernel source code []

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.10-5-powerpc/ CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "" will be used to build the module.

Is the above correct [y]

Making module
./driver_build.sh
Cisco Systems VPN Client Version BUILDVER_STRING
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserve d.

usage:
    ./driver_build.sh 'kernel_src_dir'

'kernel_src_dir' is the directory containing the linux kernel sour
ce

Failed to make module "cisco_ipsec.ko".
root@G4:/usr/src/vpnclient # uname -r
2.6.10-5-powerpc
root@G4:/usr/src/vpnclient # ./vpn_install
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserve d.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2. 6.10-5-powerpc/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.10-5-powerpc/ CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.10-5-powerpc/build" wil l be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.10-5-powerpc/build SUBDIRS=/usr/src/v pnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-p owerpc'
  CC [M]  /usr/src/vpnclient/linuxcniapi.o
In file included from /usr/src/vpnclient/linuxcniapi.c:34:
/usr/src/vpnclient/Cniapi.h:220: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:225: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:233: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:238: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:245: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:249: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:334: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:338: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:341: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:347: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:351: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:357: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:364: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:371: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:375: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:380: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:386: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:390: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:395: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:400: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:404: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:408: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:413: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:417: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:420: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:423: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:432: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:438: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:445: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:448: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:451: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:458: warning: `regparm' attribute directive ignored
In file included from /usr/src/vpnclient/linuxcniapi.c:35:
/usr/src/vpnclient/unixcniapi.h:38: warning: `regparm' attribu te directive ignored
/usr/src/vpnclient/unixcniapi.h:39: warning: `regparm' attribu te directive ignored
/usr/src/vpnclient/linuxcniapi.c:46: warning: `regparm' attrib ute directive ignored
/usr/src/vpnclient/linuxcniapi.c:52: warning: `regparm' attrib ute directive ignored
/usr/src/vpnclient/linuxcniapi.c:94: warning: `regparm' attrib ute directive ignored
/usr/src/vpnclient/linuxcniapi.c:132: warning: `regparm' attri bute directive ignored
/usr/src/vpnclient/linuxcniapi.c:192: warning: `regparm' attri bute directive ignored
/usr/src/vpnclient/linuxcniapi.c:231: warning: `regparm' attri bute directive ignored
/usr/src/vpnclient/linuxcniapi.c:289: warning: `regparm' attri bute directive ignored
/usr/src/vpnclient/linuxcniapi.c:403: warning: `regparm' attri bute directive ignored
  CC [M]  /usr/src/vpnclient/frag.o
In file included from /usr/src/vpnclient/frag.c:16:
/usr/src/vpnclient/Cniapi.h:220: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:225: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:233: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:238: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:245: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:249: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:334: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:338: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:341: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:347: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:351: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:357: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:364: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:371: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:375: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:380: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:386: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:390: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:395: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:400: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:404: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:408: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:413: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:417: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:420: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:423: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:432: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:438: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:445: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:448: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:451: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:458: warning: `regparm' attribute directive ignored
  CC [M]  /usr/src/vpnclient/IPSecDrvOS_linux.o
In file included from /usr/src/vpnclient/IPSecDrvOS_linux.c:21 :
/usr/src/vpnclient/Cniapi.h:220: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:225: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:233: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:238: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:245: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:249: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:334: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:338: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:341: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:347: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:351: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:357: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:364: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:371: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:375: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:380: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:386: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:390: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:395: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:400: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:404: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:408: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:413: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:417: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:420: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:423: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:432: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:438: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:445: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:448: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:451: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:458: warning: `regparm' attribute directive ignored
In file included from /usr/src/vpnclient/IPSecDrvOS_linux.c:22 :
/usr/src/vpnclient/IPSecDrvOSFunctions.h:64: warning: `regparm ' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOSFunctions.h:65: warning: `regparm ' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOSFunctions.h:74: warning: `regparm ' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOSFunctions.h:75: warning: `regparm ' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOSFunctions.h:76: warning: `regparm ' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOSFunctions.h:77: warning: `regparm ' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOS_linux.c:39: warning: `regparm' a ttribute directive ignored
/usr/src/vpnclient/IPSecDrvOS_linux.c:57: warning: `regparm' a ttribute directive ignored
/usr/src/vpnclient/IPSecDrvOS_linux.c:133: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOS_linux.c:166: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOS_linux.c:191: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/IPSecDrvOS_linux.c:231: warning: `regparm' attribute directive ignored
  CC [M]  /usr/src/vpnclient/interceptor.o
In file included from /usr/src/vpnclient/interceptor.c:38:
/usr/src/vpnclient/Cniapi.h:220: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:225: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:233: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:238: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:245: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:249: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:334: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:338: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:341: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:347: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:351: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:357: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:364: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:371: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:375: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:380: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:386: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:390: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:395: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:400: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:404: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:408: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:413: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:417: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:420: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:423: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:432: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:438: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:445: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:448: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:451: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/Cniapi.h:458: warning: `regparm' attribute directive ignored
/usr/src/vpnclient/interceptor.c: In function `recv_ip_packet_ handler':
/usr/src/vpnclient/interceptor.c:607: warning: passing arg 1 o f `skb_checksum_help' from incompatible pointer type
/usr/src/vpnclient/interceptor.c: In function `do_cni_send':
/usr/src/vpnclient/interceptor.c:732: warning: passing arg 1 o f `skb_checksum_help' from incompatible pointer type
  LD [M]  /usr/src/vpnclient/cisco_ipsec.o
ld: /usr/src/vpnclient/libdriver.so: Relocations in generic EL F (EM: 3)
/usr/src/vpnclient/libdriver.so: could not read symbols: File in wrong format
make[2]: *** [/usr/src/vpnclient/cisco_ipsec.o] Error 1
make[1]: *** [_module_/usr/src/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-po werpc'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
root@G4:/usr/src/vpnclient #


Does anyone have any suggestions?

---

### Post by mlomker on 2005-10-07
As far as I know, Cisco's client only supports x86 machines under linux.  VPNC isn't quite as easy to use but I have gotten it to work on i386 machines.  Is VPNC available in the Ubuntu repos?

---

### Post by calum on 2005-10-10
[QUOTE=mlomker]As far as I know, Cisco's client only supports x86 machines under linux.  VPNC isn't quite as easy to use but I have gotten it to work on i386 machines.  Is VPNC available in the Ubuntu repos?[/QUOTE]

Yes, just to let you know vpnc *is* available for Ubuntu PPC, and works well as a VPN3000 replacement for me on my Powerbook.

---

### Post by DrBubba on 2005-10-18
The "regparm" error is due to the following: vpnclient/Cniapi.h, lines 33 to 44 contain the following code:

/* the 2.6 kernel has a config option, CONFIG_REGPARM, which
   causes gcc to pass function arguments in registers. Since
   our binary-only code is compiled without this optimization,
   any functions used by the linux driver need to be declared
   with the following gcc attribute.
*/
#if defined(CNI_LINUX_INTERFACE)
#define NOREGPARM __attribute__((regparm(0)))
#else
#define NOREGPARM
#endif

which isn't configured into linux-image-2.6.20-5-powerpc (as a quick grep through /boot/config-2.6.20-powerpc came up negative on my machine).  The real problem is that the included library "libdriver.so" is a compiled x86 ELF library and so ld can't link the compiled module against it.  It's too bad as my employer (Penn State University) requires that we use this if we want to go wireless anywhere on a Penn State campus.  Sorry.

---

### Post by mlomker on 2005-10-18
> It's too bad as my employer (Penn State University) requires that we use this if we want to go wireless anywhere on a Penn State campus.  Sorry.

They probably require that you use their VPN/Pix.  They don't specifically require that VPN client, do they?  VPNC requires some scripting (mostly adds/removes from the routing table) but it did work on my Pix when I was playing with it.

---

