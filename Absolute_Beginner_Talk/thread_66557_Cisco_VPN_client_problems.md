---
title: "Cisco VPN client problems"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by Zoney on 2005-09-17
Hi!
I'm totaly fresh with Linux, wonder where i can download linux-headers-2.6.12-8-386. Because the cisco installation ask for "Directory containing linux kernel source code", and I can't find it on my computer.
I have tried downloading "linux-2.6.12.6.tar.gz", but that has to be wrong, cause I can't get the installation to work.
Anyone who can help me out?
Thanks, Øyvind.

---

### Post by cwaldbieser on 2005-09-18
[QUOTE=Zoney]Hi!
I'm totaly fresh with Linux, wonder where i can download linux-headers-2.6.12-8-386. Because the cisco installation ask for "Directory containing linux kernel source code", and I can't find it on my computer.
I have tried downloading "linux-2.6.12.6.tar.gz", but that has to be wrong, cause I can't get the installation to work.
Anyone who can help me out?
Thanks, Øyvind.[/QUOTE]
Just search for "linux-headers" in synaptic.

Also, if you enable the extra repostitories, vpnc is in there.  I have used it for some Cisco VPN sites.

---

### Post by Zoney on 2005-09-18
when i search or linux-headers i can't find my 2.6.12-8 linux-headers file :(
Only other versions..

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=Zoney]when i search or linux-headers i can't find my 2.6.12-8 linux-headers file :(
Only other versions..[/QUOTE]
Well, unless you built the kernel from source, it had to come from somewhere.  That repository also probably has the headers.  Have you switched around repositories recently?

---

### Post by minh on 2005-09-24
I've the same problem
Here is the report
hmai@ubuntu:~/My Downloads/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/usr/src/linux]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.10-5-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux" will be used to build the module.

Is the above correct [y]y

Making module
make -C /usr/src/linux SUBDIRS=/home/hmai/My Downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-source-2.6.10'
make[1]: *** No rule to make target `Downloads/vpnclient'.  Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.10'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


I've tried also to compile the kernel source, but i doesn't work :-? 
Anyone have an idea?

---

