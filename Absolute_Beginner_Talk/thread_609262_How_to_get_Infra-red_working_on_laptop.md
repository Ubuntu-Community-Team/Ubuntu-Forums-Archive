---
title: "How to get Infra-red working on laptop?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-10
Recently installed Ubuntu.
Infra-red port not working.
Does anyone know how I get this to work?
If it will help, happy to post information about my system if you give me the code to find this out...

---

### Post by PointyWombat on 2007-11-11
I don't have IR on this laptop and haven't used it for years, but try this..

Do you have the IrDA utilities installed?

# aptitude search irda-utils
i   irda-utils                                      - IrDA management and handling utilities

If not, install it:

# sudo apt-get install irda-utils

Do you see the IrDA device  on the system?

# lspci
...

Does the kernel see it?

# modprobe
...

PointyWombat

---

### Post by 01steven on 2007-11-11
Don't know if what I've done is right here:

steven@steven-laptop:~$ aptitude search irda-utils
p   irda-utils                      - IrDA management and handling utilities    
steven@steven-laptop:~$ apt-get install irda-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
steven@steven-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
steven@steven-laptop:~$ modprobe
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
steven@steven-laptop:~$

---

### Post by 01steven on 2007-11-11
Please can someone look at my settings and let me know their thoughts?
Thanks

---

### Post by 01steven on 2007-11-12
Anyone, please?

---

### Post by PointyWombat on 2007-11-13
01steven,

you need to run these commands as root:

sudo apt-get install irda-utils

as for modprobe, my error.. I should have said: "lsmod":

sudo lsmod

PointyWombat

---

### Post by 01steven on 2007-11-22
None of this has worked for me- any further suggestions please?
Sorry for the delay, just wasn't the most urgent requirement.

---

