---
title: "Compile and Configure Network Driver?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by kenwillis on 2006-11-12
Ok, I'm as new as someone can be to both Ubuntu and Linux.  I'm a network admin for Windows PCs, so I know a bit about networking and setting up computers.  I am by no means a programmer, though.

I'm trying to setup an Ubuntu system and everything seemed to be going very well.  Booted from the CD, installed the OS, browsed the net off of the install CD (network card working at this point).  Then I rebooted and booted off the hard drive ... the network card wasn't working.  No driver was loaded.

I found a Linux driver at [http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2440&SubCatID=124](http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2440&SubCatID=124)

Unfortunately, I can't figure out how in the world to compile it.  I've tried gcc <filenames.c>, but I just get a ton of errors.  I tried sudo apt-get update and sudo apt-get install build-essential, but of course I'm not connected to the Internet.

Any help is greatly appreciated.  The linux.txt below is from the driver and describes the install process for the driver.

```
**
**
**  VIA Rhine Family Fast Ethernet Adapter
**
**  Linux Driver
**
**  v5.05  Jan. 2006
**
**


Introduction:
=============

    The instructions listed below are for linux driver installation. You must
    compile the source code to generate rhinefet.o(rhinefet.ko in 2.6.x kernel,
    please remember to replace rhinefet.o with rhinefet.ko in the following
    sentences if you are using 2.6.x kernel) and use insmod command to insert 
    rhinefet.o as module.


Contents of the Subdirectory:
=============================

    linux.txt               This file.
    Makefile                Makefile for generating driver object file
    rhine_maic.c            The linux core driver source code file
    rhine_proc.c            The source to create proc entries
    rhine_wol.c             The WOL supporting source file
    rhine.h                 The extended driver header file
    rhine_proc.h            The header file for proc entries
    rhine_wol.h             The WOL supporting header file
    rhine_cfg.h             The general and basic info header file
    kcompat.h               The header file for Linux kernel version
                            compatibility.
    osdep.h                 OS depended function and macro defined
    rhine_hw.h              Rhine series MAC register supporting header file
    rhine_hw.c              shared function for accessing and configurating Rhine series MAC

Kernel Supported
================
    This driver supports linux kernel version 2.2.x, 2.4.x and 2.6.x now.

CPU Supported
=============
    This driver supports x86 and AMD64 based linux system.

Installation
============
    Please enter the following commands at the UNIX prompt. Remember, UNIX is
    case sensitive.

    1) Create a temporary directory:
        mkdir /temp

    2) Change to the temporary directory:
        cd /temp

    3) Copy driver (rhinefet.tgz) from DOS disk, (mcopy below is one tool in
       mtools, if you didn't install mtools, you can type
       'mount -t msdos /dev/fd0 /mnt' and use 'cp /mnt/rhinefet.tgz /temp'
       command to copy the driver to the temporary directory):
        mcopy a:rhinefet.tgz .

    4) untar the archive file:
        tar xzvf rhinefet.tgz
        cd src

    5) Compile the driver source files and it will generate rhinefet.o, and
       copy it to correct driver installation path (The installation directory
       is different in different kernel versions. In 2.4.x/2.6.x kernel, the path
       is /lib/modules/KERNEL_VERSION/kernel/drivers/net/, and in 2.2.x kernel,
       the path is /lib/modules/KERNEL_VERSION/net/, the KERNEL_VERSION (see
       above) means the kernel version of your Linux distribution. If you don't
       know your kernel version , please run 'uname -r' command in command
       line. The kernel version will look like '2.2.16', '2.4.2-2smp' etc.) :
        make install

    6) Check configuration file (/etc/modules.conf or /etc/conf.modules or 
       /etc/modprobe.conf, it depends on your Linux distribution) for loading 
       kernel modules. Make sure the first line below is appeared in the 
       configuration file, where # is the interface number (eg: alias eth0 
       rhinefet). If you need to set the driver options, below second line is 
       an example to set the NIC to 100Mbps fullduplex mode (remember to unmark 
       the line if it is put in the configuration file).
        alias eth# rhinefet
        #options eth# speed_duplex=2

    7) Reboot now:
        shutdown -r now

    8) Install your driver module (If the driver module is in the wrong place,
       an error message will appear, and say that can't find the driver
       module):
        insmod rhinefet.o

    9) Use ifconfig command to assign the IP address, where # is network
       interface number:
        ifconfig eth# <IP>

    10) Check the interface works:
         ping <remote_host_IP>
         
Remove intermediate files
=========================
    Please enter the following command to remove intermediate files generated
    during the driver compilation:
        make clean

Uninstallation
==============
    Please enter the following command to uninstall your driver:
        make uninstall

Bind the driver into kernel
===========================
    In some applications (e.g. embedded OS), driver should be bound into the
    kernel. The module installation/uninstallation describled in the above
    sections are not appropriate. Below is the steps for binding driver in
    kernel 2.4.x as an example:

    1) Create a temporary directory:
        mkdir /temp

    2) Change to the temporary directory:
        cd /temp

    3) Copy driver (rhinefet.tgz) from DOS disk, (mcopy below is one tool in
       mtools, if you didn't install mtools, you can type
       'mount -t msdos /dev/fd0 /mnt' and use 'cp /mnt/rhinefet.tgz /temp'
       command to copy the driver to the temporary directory):
        mcopy a:rhinefet.tgz .

    4) untar the archive file:
        tar xzvf rhinefet.tgz

    5) Change to the kernel source directory:
        cd /usr/src/<kernel source>/driver/net

    6) Create a directory for rhine family adapter driver and change to it:
        mkdir rhinefet
        cd rhinefet

    7) Copy driver source form temporary directory to it:
        cp /temp/rhinefet/* .

    8) Replace the default Makefile with new Makefile with below 4 line content
       (the Makefile used for driver binding into kernel is different with
       the default one).
       O_TARGET := rhinefet.o
       obj-y    := rhine_main.o rhine_proc.o rhine_wol.o rhine_hw.o
       obj-m    := $(O_TARGET)
       include  $(TOPDIR)/Rules.make

    9) Add the rhinefet information to /usr/src/<kernel source>/drivers/net/Makefile:
       (add the lines with # in the head)
             ...
             ...
        subdir-$(CONFIG_E100) += e100
        #subdir-$(CONFIG_RHINEFET) += rhinefet
             ...
             ...
        ifeq ($(CONFIG_E100),y)
           obj-y += e100/e100.o
        endif
        #ifeq ($(CONFIG_RHINEFET),y)
        #   obj-y += rhinefet/rhinefet.o
        #endif

    10) Add the rhinefet information to /usr/src/<kernel source>/drivers/net/Config.in:
        (add the lines with # in the head)
             ...
             ...
        mainmenu_option next_comment
        comment 'Ethernet (10 or 100Mbit)'
        bool 'Ethernet (10 or 100Mbit)' CONFIG_NET_ETHERNET
             ...
             ...
        #dep_tristate   '    VIA Rhine Family Fast Ethernet Adapter support' CONFIG_RHINEFET $CONFIG_PCI
             ...
             ...
        endmenu

    11) Now, when you use following command, make menuconfig or make xconfig,
        you will find a new device in 'Network device support'->'Ethernet(10 or 100Mbits)'.
        Its name is 'VIA Rhine Family Fast Ethernet Adapter support'.

Note
====
    1) Make sure the link file /usr/src/linux (or /usr/src/linux-2.4) is linked
       to correctly kernel sources directory (eg: if you run 'uname -r', it
       appears "2.4.2-2", then the link file must be linked to
       /usr/src/linux-2.4.2 directory, or you will fail in compiling),
       and make sure there are kernel header files in /usr/src/linux/include
       directory (or /usr/src/linux-2.4/include), we need kernel header files
       in compling.

    2) If you can't install driver in SUSE Linux using insmod or modprobe
       commands, and error messages appear (see below), please run 'uname -r'
       in command line. And make sure the result of 'uname -r' (eg: 2.4.2-4GB)
       is the same with the definition of UTS_RELEASE in
       /usr/src/linux/include/linux/version.h. If not, please modify the
       definition of UTS_RELEASE in /usr/src/linux/include/linux/version.h.

         rhinefet.o: kernel-module version mismatch
             rhinefet.o was compiled for kernel version 2.4.2
             while this kernel is version 2.4.2-4GB.

    3) Make sure that your kernel is built with network, fast_ethernet
       and module support. Otherwise, you have to rebuild your kernel (see
       below).
        1. Go to /usr/src/linux (or /usr/src/linux-2.4) directory:
            cd /usr/src/linux
        2: Run 'make menuconfig' or 'make config' in text mode, or 'make
           xconfig' in graphic mode.
        3: Mark the options list above.
        4: Exit and rebuild your kernel:
            make dep;make clean;make bzImage
           The file 'bzImage' will be at /usr/src/linux/arch/i386/boot/bzImage
        5: Modify /etc/lilo.conf.(this file specifies where kernel image is)
        6: Run 'lilo'
        7: Reboot, and select the correct kernel image to boot your system.

    4) You can use the utility (like netconfig, linuxconf) in your Linux
       distribution to set your network parameters(like ip,gateway). These
       parameters will be used at boot time. The following is the demonstration
       to show how to use linuxconf (it's a utitlity in RedHat Linux 6.x) set
       the network paramters.
       1. Run linuxconf:
           linuxconf
       2. Enter setting in the Config/Networking/Client tasks/Basic host information/
          and fill out the following information. Where 'xxx' is the IP address
          what you have.
                    IP address:    xxx.xxx.xxx.xxx
                    Netmask:       255.255.255.xxx
                    Net device:    eth0
                    Kernel module: rhinefet

    5) If you can't install driver at boot time.
       If you can install your driver using insmod command, but you can't
       install it at boot time, please check whether the driver is in the
       correct directory (eg: /lib/modules/2.2.XXX/net/), and check the
       /lib/modules/2.2.XXX/modules.dep file, it must include the following
       line:
            /lib/modules/2.2.XXX/net/rhinefet.o:

       You can insert this line using depmod command or insert it manually.
       Also, you must consult your Linux distribution installation guide
       and learn how to set the IP address of your network interface and
       up it at boot time.

    6) If you can't compile this driver, and parse error messages appear,
       please make sure your source code text format is right. You must convert
       your source code text format from MS-DOS to UNIX, as show below (see
       Solution 1 and 2).
       Make sure the files in floppy disk are not rhinefet.tgz file. They must
       be the source code text files (5 files), rhinefet.tgz is not a text file
       , so it can't be converted.

        Solution1:
            If you use mcopy command to copy your driver from floppy disk to
            linux, you can type:
                mcopy -t a:\* .
            then it will convert the format for you.

        Solution2:
            If you use mount command to mount floppy disk to linux, you can
            type:
                mount -t vfat -o conv=t /dev/fd0 /mnt/floppy
            then, when you copy files from /mnt/floppy, these files format will
            be right.

Module Parameter:
=================
The following parameters can be set when we install the driver module. You can 
add this parameters when you execute 'insmod' or 'modprobe' command to install 
the driver (as below).
    insmod rhinefet.o parameter=value1,value2,value3,...
For example, if you have 3 NIC cards, and you want to set the speed_duplex 
paramter value of them. You can type the following command to set it.
    insmod rhinefet.o speed_duplex=1,2,3
Then, the parameter value of first card will be 1 (100Mbps half duplex mode), 
the second card will be 2 (100Mbps full duplex mode), and the third card will 
be 3 (10Mbps half duplex mode). Remember, our driver only support 8 cards 
parameter setting.

1) speed_duplex
   speed_duplex[] is used for setting the speed and duplex mode of NIC.
   Value:
       0: indicate autonegotiation for both speed and duplex mode (Default).
       1: indicate 100Mbps half duplex mode
       2: indicate 100Mbps full duplex mode
       3: indicate 10Mbps half duplex mode
       4: indicate 10Mbps full duplex mode

2) RxDescriptors
   RxDescriptors[] is used for setting the number of receive descriptors.
   Value:
       64-128 (Default value: 64)

3) TxDescriptors
   TxDescriptors[] is used for setting the number of transmit descriptors.
   Value:
       16-128 (Default value: 64)

4) enable_tagging (For management adapter only)
   enable_tagging[] is used for enabling VLAN ID setting and enabling
   priority transmit.
   Value:
       0: disable VID setting and priority transmit (Default).
       1: enable VID setting and priority transmit.

5) VID_setting (For management adapter only)
   VID_setting[] is used for setting the VLAN ID of NIC.
   Value:
       0: default VID.
       1-4094: other VIDs.

6) rxcsum_offload (For management adapter only)
   rxcsum_offload[] is used for setting the receive checksum offload ability
   of NIC.
   Value:
       0: disable
       1: enable (default)

7) txcsum_offload (For management adapter only)
   txcsum_offload[] is used for setting the transmit checksum offload ability
   of NIC.
   Value:
       0: disable (default)
       1: enable

9) flow_control
   flow_control[] is used for setting the flow control ability of NIC. Only
   option 1(default) set flow control ability according to the auto-negotiation
   result. Option 2, 3 are the forced flow control mode and they don't see the
   auto-negotiation result.
   Value:
       1: hardware deafult (Default). Don't change the hardware register value
          in MII ANAR.
       2: disable flow control.
       3: enable flow control.

10) IP_byte_align
    IP_byte_align[] is used for IP header DWORD byte aligned (For IPVS environment).
    (In some enviroment, the IP header should be DWORD byte aligned,or the packet
    will be droped when we receive it. (eg: IPVS))
    Value:
        0: indicate the IP header won't be DWORD byte aligned (Default).
        1: indicate the IP header will be DWORD byte aligned.

11) ValPktLen
    ValPktLen[] is used for controlling driver to receive or drop
    the frame with invalid layer 2 length.
    Value:
        0: Receive frame with invalid layer 2 length.
        1: Drop frame with invalid layer 2 length.

12) wol_opts
    wol_opts[] is used for controlling wake on lan behavior of NIC.
        0: Wake up if recevied a magic packet. (Default)
        1: Wake up if link status is on/off.
        2: Wake up if recevied an arp packet.
        4: Wake up if recevied any unicast packet.
        Those value can be sumed up to support more than one option.
```

---

### Post by podunk on 2006-11-12
I have Via RHine and it  worked out of the box. The fact that yours worked on the CD suggests either it couldn't read the file properly during the install or you have a setting wrong somewhere.

Click System>Administration>Networking. Click your card (should be eth0) and see if you can activate it.

If not, I'd suggest making a new install CD - burn it dead s-l-o-w and redoing the install.

If you want to get down and dirty with Linux compiling drivers is most likely the best way to go thoough. :-)

---

### Post by Sef on 2006-11-12
> Unfortunately, I can't figure out how in the world to compile it

To compile you need to install build-essential.

sudo aptitude update

sudo aptitude install build-essential

---

### Post by kenwillis on 2006-11-12
Thanks for the responses and help.  They're very appreciated!

> To compile you need to install build-essential.

sudo aptitude update

sudo aptitude install build-essential

Is there a way to get those without it having to go to the Internet to look for them?  I tried that and it just got errors there as well.

> Click System>Administration>Networking. Click your card (should be eth0) and see if you can activate it.

Actually, there is only a modem listed there.  That's my problem it didn't load the drivers for the NIC.  I'll reburn the CD and try to reload if I can't find something else pretty soon.

---

