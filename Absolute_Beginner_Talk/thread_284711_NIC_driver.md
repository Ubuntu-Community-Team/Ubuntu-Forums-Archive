---
title: "NIC driver"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-26
I am trying to install a NIC driver and I'm getting nowhere fast. I pop the floppy in and the README.TXT says to type in make org or make org24(if I have kernel 2.4). I have no clue what my kernel version is but it must be fairly new since I am running Dapper. I am guessing 2.4. Anyway, I type in make org24 and this is roughly what comes back:


make: No rule to make dm9xs.c: **stop**

help! I don't understand what this means....](*,)

---

### Post by po0f on 2006-10-26
saintj0n,

Is the card plugged in?  What does lspci say about it?  You should install linux-header-`uname -r` and/or linux-source-`uname -r` if you haven't done so already.

And are you sure you have to build the module from the driver disk provided?  If so, please post the contents of the floppy and the Makefile.

---

### Post by saintj0n on 2006-10-26
Here is the Makefile. The .c file is *way* too big to post. I would have to segment it into several messages.

##================================================================
##     Davicom Semiconductor Inc.  		03/08/2001	
##   --------------------------------------------------------
## Description:
##              Compile driver dmfe.c to dmfe.o
##              Compile driver dm9xs.c to dm9xs.o
##
## Modification List:
## 03/08/2001	Compile option for dm9xs.c or dmfe.c
## 09/05/2000	Fixed SMPFALGS wrong on smp & smp_mod
## 08/02/2000	Changed some description string & include file path
## 07/25/2000	Append smp_mod and changed some descriptions
## 01/25/2000	by Sten Wang
##================================================================

CC	= gcc
CFLAGS  = -DMODULE -D__KERNEL__ -I/usr/src/linux/include -Wall -Wstrict-prototypes -O6 -c
MFLAGS  = -DMODVERSIONS
SMPFLAGS = -D__SMP__

##=============================================
## Default Compiler: make all
##=============================================
all:		org


##=============================================
## One processor and normal kernel: make org
##=============================================
org:	dmfe.c \
	Makefile
	$(CC) $(CFLAGS) dmfe.c

org24:	dm9xs.c \
	Makefile
	$(CC) $(CFLAGS) dm9xs.c


##=============================================
## Set version info. on all module symbol
##     : make mod
##=============================================
mod:	dmfe.c \
	Makefile
	$(CC) $(MFLAGS) $(CFLAGS) dmfe.c

mod24:	dm9xs.c \
	Makefile
	$(CC) $(MFLAGS) $(CFLAGS) dm9xs.c


##=============================================
## Symmetric Multi Processor(SMP)
##     : make smp
##=============================================
smp:	dmfe.c \
	Makefile
	$(CC) $(SMPFLAGS) $(CFLAGS) dmfe.c

smp24:	dm9xs.c \
	Makefile
	$(CC) $(SMPFLAGS) $(CFLAGS) dm9xs.c


##=============================================
## SMP & Set all version info. on all module symbols
##     : make smp_mod
##=============================================
smp_mod:dmfe.c \
	Makefile
	$(CC) $(SMPFLAGS) $(MFLAGS) $(CFLAGS) dmfe.c

smp_mod24:dm9xs.c \
	Makefile
	$(CC) $(SMPFLAGS) $(MFLAGS) $(CFLAGS) dm9xs.c


##=============================================
## Clean all object file
##=============================================
clean:			
			rm *o
That's all of it.
Thanks......:cool:

---

### Post by saintj0n on 2006-10-26
....and here is the README.TXT:

  DAVICOM Semiconductor Inc.				04/20/2001



        A Davicom DM9009/DM9102/DM9102A/DM9102A+DM9801(HomeRun)/

        DM9102A+DM9802(LongRun) NIC fast ethernet driver for Linux. 

        Copyright (C) 1997  Sten Wang



        This program is free software; you can redistribute it and/or

        modify it under the terms of the GNU General Public License

        as published by the Free Software Foundation; either version 2

        of the License, or (at your option) any later version.



        This program is distributed in the hope that it will be useful,

        but WITHOUT ANY WARRANTY; without even the implied warranty of

        MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the

        GNU General Public License for more details.



	Now dmfe.c is for kernel 2.2.x and dm9xs.c is for kernel 2.4.x.

	If you use kernel 2.4.x, please use dm9xs.c to instead dmfe.c on

	the following.



  A. Compiler command:



     A-1: For normal single processor kernel

          "gcc -DMODULE -D__KERNEL__ -I/usr/src/linux/net/inet -Wall 

            -Wstrict-prototypes -O6 -c dmfe.c"



     A-2: For single processor and set version info on all module symbol

          "gcc -DMODULE -DMODVERSIONS -D__KERNEL__ -I/usr/src/linux/net/inet 

            -Wall -Wstrict-prototypes -O6 -c dmfe.c"



     A-3: For multiple processors(SMP) and set ver. info. on all module symbol

          "gcc -D__SMP__ -DMODULE -DMODVERSIONS -D__KERNEL__ -I/usr/src/linux

           /net/inet -Wall -Wstrict-prototypes -O6 -c dmfe.c"



	Note: O of -O6 is a capital "o", not a "0".

	    



  B. How to compile driver 

  

     B-1: Login by supervisor

     B-2: Copy dmfe.c and Makefile into your HD. You can make a new directoty 

          to put.

     B-3: Keep driver source file name as "dmfe.c" and makefile name as 

	  "Makefile"

     B-4: You can type the following command to compile driver. Please according

     	  to your system to pick one.

     		make org	;;Without SMP & Set version info on module

				;;<For example> Redhat6.0

     		make mod	;;Set version info on all module symbol

				;;<For example> Redhat6.1/6.2,

				;;		Mandrake6.1/7.0/7.1,

				;;		Caldera2.3

     		make smp	;;symmetric multi-processing(SMP) support

				;;

     		make smp_mod	;;SMP & Set version info on module

				;;

		make org24	;;Compiled dm9xs.c

		make mod24	;;Compiled dm9xs.c

		make smp24	;;Compiled dm9xs.c

		make smp_mod24	;;Compiled dm9xs.c

     	

     	  Or you can type above compiler command to compile driver.

     		

     	Note: Please check you must have the right kernel source on 

     	      "/usr/src/linux".





  C. The following steps teach you how to activate NIC:



     C-1: A simple and temporary method

     

        1. Used the upper compiler command to compile dmfe.c



        2. Insert dmfe module into kernel

           "insmod dmfe"        ;;Auto Detection Mode (Suggest)

           "insmod dmfe mode=0" ;;Force 10M Half Duplex

           "insmod dmfe mode=1" ;;Force 100M Half Duplex

           "insmod dmfe mode=4" ;;Force 10M Full Duplex

           "insmod dmfe mode=5" ;;Force 100M Full Duplex

           "insmod dmfe mode=0x10" ;;Force 1M HomePNA

           "insmod dmfe SF_mode=1" ;;VLAN Enable

           "insmod dmfe SF_mode=2" ;;Flow Control Enable

           "insmod dmfe SF_mode=4" ;;TX Pause Packet Enable



	   NOTE:1. SF_mode can be a combination of 3 special mode.

		2. You can type "man insmod" to see more description.



        3. Config a dm9102 network interface

           "ifconfig eth0 172.22.3.18"

                          ^^^^^^^^^^^ Your IP address



	   NOTE: You can type "man ifconfig" to see more description.



        4. Activate the IP routing table. For some distributions, it is not

           necessary. You can type "route" to check.



           "route add default netmask 255.255.255.0 eth0"



	   NOTE: You can type "man route" to see more description.





        5. Well done. Your DM9102 adapter actived now.



	Note. This is a temporary method. After you reboot the system, you

	      will lost the setting.





     C-2: For Mandrake/Redhat, You can use the following to Activate NIC

	

	1. login your system used the superuser

	2. (Mandrake7.0)

   		rename dmfe_m70.o to dmfe.o and copy dmfe.o into

	  	/lib/modules/2.2.14-15mdk/net to overwrite the old dmfe.o.

	   or(Mandrake6.1)

   		rename dmfe_m61.o to dmfe.o and copy dmfe.o into

	  	/lib/modules/2.2.13-7mdk/net to overwrite the old dmfe.o.

	   or(RedHat6.2)

   		rename dmfe_r62.o to dmfe.o and copy dmfe.o into

	  	/lib/modules/2.2.14-5.0/net to overwrite the old dmfe.o.

   	   or(RedHat6.1)

   		rename dmfe_r61.o to dmfe.o and copy dmfe.o into

	  	/lib/modules/2.2.12-20/net to overwrite the old dmfe.o.

	   or(RedHat6.0)

	   	rename dmfe_r60.o to dmfe.o and copy dmfe.o into

	  	/lib/modules/2.2.5-15/net to overwrite the old dmfe.o.

    

	3. execute "linuxconf".

	4. Then select Config->Networking->Client tasks ->Basic host information

	5. Fill your IP address, netmask,

	   net device = eth0

	   kernel module = dmfe

	6. press <Accept> to confirm and exit this setting

	7. press <quit> exit the main menu

	8. Now it displays "Status of the system" menu. Select <Activate the

	   changes> to active the new setting and exit.

	9. reboot your system and kernel will automatically load driver and

	   active network.

	10. try to ping other host to test your NIC.





     C-3: For Caldera or others, You can use the following to Activate NIC

	  permanently. Please try C-1 firstly. After your NIC works on C-1

	  method, you do the following to active NIC permanently.

	  

	1. copy dmfe.o to your kernel network module directory

	   <eg>

		for Caldera 2.3:

			cp dmfe.o /lib/modules/2.2.10/net



	2. put C-1 manual command into file "/etc/rc.d/rc.local" or 

	   "/etc/rc.d/rc.inet1".

	   <eg>

		for Caldera 2.3:

		    add the following 3 line into rc.local

			insmod /lib/modules/2.2.10/net/dmfe.o

			ifconfig xxx.xxx.xxx.xxx netmask 255.255.255.0 eth0

			route add default eth0



	3. reboot your system







   D. Object files description:



	dmfe_r70.o:		For Redhat 7.0, Kernel 2.2.16-22

    	dmfe_r62.o:		For Redhat 6.2, kernel version 2.2.14-5.0

	dmfer61c.o:		For Redhat 6.1+CLE0.8, kernel 2.2.12-20

	dmfe_r60.o:		For Redhat 6.0, Kernel 2.2.5-15



	dmfe_m71.o:		For Mandrake 7.1, kernel 2.2.15-4mdk

	dmfe_m70.o:		For Mandrake 7.0, Kernel 2.2.14-15mdk

	dmfe_m61.o:		For Mandrake 6.1, Kernel 2.2.13-7mdk



	dmfe_c23.o:		For Caldera 2.3, kernel 2.2.10



	dmfe2217.o:		For Kernel 2.2.17. Without SMP and

				did not set version on kernel module.

	dmfe2218.o:		For Kernel 2.2.18. Without SMP and

				did not set version on kernel module.

	dm9xs241.o:		For Kernel 2.4.1. Without SMP and

				did not set version on kernel module.

	dm9xs242.o:		For Kernel 2.4.2. Without SMP and

				did not set version on kernel module.

	dm9xs243.o:		For Kernel 2.4.3. Without SMP and

				did not set version on kernel module.

	

	



        If you can make sure your kernel version, you can rename

        to dmfe.o and directly use it without re-compiling.







  DAVICOM Web-Site: [www.davicom.com.tw](www.davicom.com.tw)



  Author: Sten Wang, 886-3-5798797-8517, E-mail: [email]sten_wang@davicom.com.tw[/email]


Later!

---

### Post by po0f on 2006-10-27
saintj0n,

First of all, unless you explicitly installed a 2.4.* kernel, you are running 2.6.*.

In the Makefile, where CFLAGS is defined, can you confirm that /usr/src/linux/include points to header files for the kernel that you're building this for, ie `uname -r`?

Ok, I just noticed the copyright on the Makefile.  :rolleyes:   I don't think you're going to get this to work with a 2.6.* kernel.  Are you sure that a module isn't loaded for this when you boot up your box?

---

### Post by saintj0n on 2006-10-28
I'm not sure now what's up with it. I used the same linux dvd(dapper) and plugged the same nic into a different pci slot in a different pc and voila! It works now, maybe it was a motherboard issue...:rolleyes:

---

