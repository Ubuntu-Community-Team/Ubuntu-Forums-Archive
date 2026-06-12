---
title: "is there another way for wireless"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by katarot on 2006-03-17
1.
      sudo apt-get install ndiswrapper-utils
   2.
      cd (location of windows drivers)
   3.
      sudo ndiswrapper -i (name of windows driver).inf
   4.
      sudo ndiswrapper -m
   5.
      sudo depmod -a
   6.
      sudo modprobe ndiswrapper
   7.
      sudo ifup wlan0 
ignoring unrecgonised interface
martin@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:22:8E:B7:91
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:0F:9F:6D:D5:97
          inet addr:82.40.234.90  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:9fff:fe6d:d597/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:840893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:56583776 (53.9 MiB)  TX bytes:1633798 (1.5 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6268779 (5.9 MiB)  TX bytes:6268779 (5.9 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
if this is the only way then im screwed

---

### Post by chuckyp on 2006-03-17
What type of network card do you have. i.e. what model and manufacturer.

---

### Post by sailor2001 on 2006-03-17
the way I do it that works quite eazy:
cdDesktop
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i NET8180.INF
sudo ndiswrapper -l
sudo dhclient
sudo ndiswrapper -m

disregard comments (can't find driver)

---

### Post by sailor2001 on 2006-03-17
space between cd and Desktop

---

### Post by Brunellus on 2006-03-17
strange.  you have two eth interfaces.  one of them might be your wireless card.  what is the output of 

iwconfig eth1

---

### Post by katarot on 2006-03-17
no eth1 is there because  i connected my laptop directly to the modem and set that connection 

i have tried everything with this i press sudo ndiswrapper -l 
and it says hardware present and driver present 
then i go to the network and it is not there  so i cant change it 
also when i type sudo ifup wlan0 i get
Ignoring unknown interface wlan0=wlan0.
im clueless

---

### Post by Brunellus on 2006-03-17
sudo ifup -a

---

### Post by katarot on 2006-03-17
ok here is my error messages from when i done it the first time 
martin@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl   invalid driver!
bcmwl5  driver present, hardware present
martin@ubuntu:~$ sudo ndiswrapper -e bcmwl
martin@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
martin@ubuntu:~$ sudo depmod -a
sudo modprobe ndiswrapper
tail /var/log/messages
martin@ubuntu:~$ sudo modprobe ndiswrapper
martin@ubuntu:~$ tail /var/log/messages
Mar 17 20:38:53 localhost kernel: [4304814.554000] DMA: 1*4kB 1*8kB 1*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1052kB
Mar 17 20:38:53 localhost kernel: [4304814.554000] Normal: 47*4kB 16*8kB 0*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 2076kB
Mar 17 20:38:53 localhost kernel: [4304814.554000] HighMem: empty
Mar 17 20:38:53 localhost kernel: [4304814.554000] Swap cache: add 2006, delete 2006, find 0/0, race 0+0
Mar 17 20:38:53 localhost kernel: [4304814.554000] Free swap  = 0kB
Mar 17 20:38:53 localhost kernel: [4304814.554000] Total swap = 8024kB
Mar 17 20:38:56 localhost gconfd (root-10119): GConf server is not in use, shutting down.
Mar 17 20:38:56 localhost gconfd (root-10119): Exiting
Mar 17 20:39:13 localhost kernel: [4304836.203000] hdb: status error: status=0x50 { DriveReady SeekComplete }
Mar 17 20:39:13 localhost kernel: [4304836.203000] ide: failed opcode was: unknown
martin@ubuntu:~$

and heres what i got when i did subo ifup -a
martin@ubuntu:~$ sudo ifup -a
ifup: interface lo already configured
ifup: interface eth1 already configured
martin@ubuntu:~$

whats wrong here

---

### Post by katarot on 2006-03-17
i think if i could just get it to display it to show it is there but it is not even showing it 
eth0
l0
eth1
sit0
that is the only ones i get i need wlan0 to show there then i could get this 
its like it dosent exist

---

### Post by Brunellus on 2006-03-17
iwconfig eth0

---

### Post by katarot on 2006-03-17
i was looking about and i found my driver 

  Additional Installation Notes for Various Linux Distributions
                       Broadcom BCM4400 Linux Driver
                              Version 3.0.7
                                10/31/2003

                          Broadcom Corporation
                          16215 Alton Parkway,
                          Irvine, CA 92619-7013

                Copyright (c) 2000-2003 Broadcom Corporation
                           All rights reserved


Table of Contents
=================

  Introduction
  Limitations
  Prerequisites
  Prepare Kernel Source Tree (United Linux 1.0 Distributions)


Introduction
============

This file contains additional installation notes for the Broadcom bcm4400
Linux driver that are specific to certain Linux distributions. General
installation notes are contained in README.TXT.


Limitations
===========

The current version of the driver has been tested on the following Linux
distributions:

Distributions for i386:

   Red Hat 8.0, 9.0 and 2.1AS
   UnitedLinux 1.0 based distributions (UnitedLinux 1.0, SuSE SLES8, 8.1,
      and SCO 4.0)
   UnitedLinux 1.0 SP1
   Mandrake 9.0
 

Prerequisites
=============

In order to compile your Broadcom Linux driver, you must first
have a properly compiled kernel source tree which matches your running
kernel.  You must also have a working C/C++ compiler and all the associated
dependencies installed before attempting to compile the driver.
 
On Red Hat distributions, if you have opted for a custom installation, you
need to select "Development Tools" and "Kernel Development" to install
the necessary tools and kernel source tree.
   
On United Linux based distributions, you must change the software packages
installed by default when presented with the Installation Settings.  Under
software selelction, select "Detailed Selection".  In this area ensure that
"C/C++ Compiler and Tools" is selected.  This should install the C/C++
compiler as well as the kernel-source files.
   
For further assistance, please review your Linux documentation. 
    
      
Prepare Kernel Source Tree (United Linux 1.0 Distributions)
===========================================================
       
The following instructions pertain only to United Linux 1.0 based
distributions (SuSE SLES8, SuSE 8.x, SCO4.0, etc.)  These steps are not
needed for Red Hat, Mandrake and other similar distributions.
        
1. Prepare the kernel source tree.  These steps are necessary in order to
   compile a driver that will match your running kernel.
	
   cd /usr/src/linux-<kernel_version>.SuSE
   cp /boot/vmlinuz.config .config
   cp /boot/vmlinuz.version.h include/linux/version.h
   cp /boot/vmlinuz.autoconf.h include/linux/autoconf.h
   make oldconfig
   make dep

2. Now build and install the Broadcom Linux driver using either the rpm or
   tar archive installation files. The procedures are found in README.TXT.

and there was alot more files 
how do i set this up

---

### Post by katarot on 2006-03-17
confused 
1. Create a directory and extract the files:

   tar xvzf bcm4400-<version>.tar.gz # here im sure i use sudo modprobe 
#did this one just made a new folder and extracted files to it
2. Build the driver bcm4400.o as a loadable module for the running kernel:

   cd src
   make
 # here im sure i use sudo modprobe 


3. Test the driver by loading it: 

   insmod bcm4400.o
#ok i know what to do here 
4. Install the driver and man page:

   make install
#confused here tho

---

