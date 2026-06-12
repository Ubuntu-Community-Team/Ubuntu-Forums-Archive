---
title: "i need help installing USB LAN"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by chocoliya on 2007-09-04
hi!

i need help in installing the driver for my USB LAN....i'm not really familiar on how to compile/install the driver installer so can anyone explain this readme.txt that was in the driver folder to me very simply?

===========
SHANTOU Semiconductor Inc.				05/16/2003

        A SHANTOU ST268 USB Fast Ethernet driver for Linux. 
        Copyright (C) 1997  Sten Wang

        This program is free software; you can redistribute it and/or
        modify it under the terms of the GNU General Public License
        as published by the Free Software Foundation; either version 2
        of the License, or (at your option) any later version.

        This program is distributed in the hope that it will be useful,
        but WITHOUT ANY WARRANTY; without even the implied warranty of
        MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
        GNU General Public License for more details.

  A. Compiler command:

     A-1: For normal single processor kernel
          "gcc -DMODULE -D__KERNEL__ -I/usr/src/linux/include -Wall 
            -Wstrict-prototypes -O6 -c ST268.c"

     A-2: For single processor and set version info on all module symbol
          "gcc -DMODULE -DMODVERSIONS -D__KERNEL__ -I/usr/src/linux/include
            -Wall -Wstrict-prototypes -O6 -c ST268.c"

     A-3: For multiple processors(SMP) and set ver. info. on all module symbol
          "gcc -D__SMP__ -DMODULE -DMODVERSIONS -D__KERNEL__ -I/usr/src/linux
           /include -Wall -Wstrict-prototypes -O6 -c ST268.c"

     	Note: O of -O6 is a capital "o", not a "0".
	    

  B. How to compile driver 
  
     B-1: Login by supervisor
     B-2: Copy ST268.c and Makefile into your HD. You can make a new directoty
          to put.
     B-3: Keep driver source file name as "ST268.c" and makefile name as 
	  "Makefile"
     B-4: You can type the following command to compile driver. Please according
     	  to your system to pick one.
     		make org	;;Without SMP support 
     		make mod	;;Set version info on all module symbol
     		make smp	;;symmetric multi-processing(SMP) support
     		make smp_mod	;;SMP & Set version info on module

     	  Or you can type above compiler command to compile driver.
     		
     	  Note: Please check you must have the right kernel source on 
     	      "/usr/src/linux".


  C. The following steps teach you how to activate NIC:

     C-1: A simple and temporary method

        1. Used the upper compiler command to compile ST268.c

        2. Insert ST268 module into kernel
           "insmod ST268.o"           ;;Auto Detection Mode (Suggest)
           "insmod ST268.o mode=0"    ;;Force 10M Half Duplex
           "insmod ST268.o mode=1"    ;;Force 100M Half Duplex
           "insmod ST268.o mode=4"    ;;Force 10M Full Duplex
           "insmod ST268.o mode=5"    ;;Force 100M Full Duplex

	   NOTE: You can type "man insmod" to see more description.

        3. Config a ST268 network interface
           "ifconfig eth0 172.22.3.18"
                          ^^^^^^^^^^^ Your IP address

	   NOTE: 1. You can type "man ifconfig" to see more description.
		 2. If eth0 has been used, you should use eth1 instead.

        4. Activate the IP routing table. For some distributions, it is not
           necessary. You can type "route" to check.

           "route add default netmask 255.255.255.0 eth0"

	   NOTE: 1. You can type "man route" to see more description.
		 2. If eth0 has been used, you should use eth1 instead.

        5. Well done. Your ST268 adapter actived now.

	Note. This is a temporary method. After you reboot the system, you
	      will lost the setting.


     C-2: For Redhat, You can use the following to Activate NIC
	
	1.  login your system used the superuser.
	2.  copy ST268.o into	/lib/modules/2.4.x/kernel/drivers/net/
	3.  add the new line with "alias eth0 ST268" in "/etc/module.conf". 
	4.  execute "netconfig -d eth0".
	5.  Fill your IP address, netmask and gateway
	6.  press <ok> to confirm and exit this setting
	7   reboot

	Note. If eth0 has been used, you should use eth1 instead.

===========

i tried copying ST268 and also made the MakeFile and then saved them in the desktop...when i pasted 
[I]gcc -DMODULE -D__KERNEL__ -I/usr/src/linux/include -Wall 
            -Wstrict-prototypes -O6 -c ST268.c[/I] in the terminal it saif file not found =(

it's frustrating going back and forth between xp and ubuntu because i don't have inet access in ubuntu....

p.s.

my pci slots are all broken (always network cable unplugged) that's why i resorted to a USB LAN....this is in case you'll suggest i use an ethernet card instead.

any help will be appreciated...thnx! :KS

---

### Post by mlentink on 2007-09-04
I'm not an expert on installing drivers form source at all, so I might be wrong.

Seems to me you could have used this:
```
sudo cd Desktop
```
to get into your desktop folder, and then
```
sudo make smp_mod
```
as per the instructions

PLease be aware that adding such a driver to the kernel will be lost when a newer kernel is installed. You would have to do the same thing again

---

### Post by chocoliya on 2007-09-04
hi! thanks for the response =)

i tried doing your suggestion but it didn't work...

[IMG]http://anna.leah.m.googlepages.com/Screenshot.jpg[/IMG]

thanks anyways ;p

---

### Post by mlentink on 2007-09-04
Like I said, I'm not an expert. It seems to me that makefile is not as straightforward as it should be, but fixing it is beyond my level of ability. Sorry...

Someone else?

---

### Post by chocoliya on 2007-09-04
i really appreciate your effort though =)

so....

anyone? other ideas? help!

---

