---
title: "HP Mini 210-2100 Webcam Conundrum"
date: 2012-05-28
forum: Any Other OS
---

### Post by jmartinka on 2012-05-28
I am running Linux Mint. The issue is that the webcam does not show up  in 'lsusb', nor in Cheese, Skype, or anyhing I have tried. My wife has  the same EXACT laptp with the same specs.

When I use 'lsusb' on my laptop the result looks like this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

When I use the same command on my wife's laptop it looks like this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1234:5678 Unknown
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 004: ID 174f:112f Syntek

This  makes me assume that the webcam on her system (and therefore the one  that should be installed on mine) is a Symtek driver. I found the driver  online and tried to compile it but I keep getting the following errors:  

make -C /lib/modules/3.2.0-23-generic/build SUBDIRS=/home/joseph/Downloads/stk11xx-2.1.0 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /home/joseph/Downloads/stk11xx-2.1.0/stk11xx-usb.o
/home/joseph/Downloads/stk11xx-2.1.0/stk11xx-usb.c: In function ‘usb_stk11xx_probe’:
/home/joseph/Downloads/stk11xx-2.1.0/stk11xx-usb.c:793:2:  error: implicit declaration of function ‘init_MUTEX’  [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/joseph/Downloads/stk11xx-2.1.0/stk11xx-usb.o] Error 1
make[1]: *** [_module_/home/joseph/Downloads/stk11xx-2.1.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [driver] Error 2

   			  			I do not understand. I have tried everything I  can think of. I have tried installing the Syntek drivers, I have tried  gspca, I have tried to find SOMEONE who has had and solved an issue even  slightly similar to mine, but with no success. I do not want to go back  to Windows because of this, but I really wish there was a solution so  that I can say that my transition has worked 100%. 

Is there  anything I can do to fix this? As I have stated my wife has the same  exact laptop and she is running Mint off of a flash drive with no  issues. She still has Windows on her system as she has not made the full  switch to Mint, but she really wants to. I am holding back just in case  there is some file or driver I can get from her either from Windows or  Linux that I can install to try and get this issue resolved, but I can  not think of a way to do it. Is there ANYONE who has any suggestions for  me?

---

### Post by Perfect Storm on 2012-05-29
Moved to Other OS/Distro Talk.

---

### Post by jmartinka on 2012-05-29
When the camera does show up in 'lsusb' the entry looks like this. 

Bus 001 Device 003: ID 5986:0313 Acer, Inc.

Any suggestions for where to look for drivers? I have tried to Google the Device and Vendor ids and come up with nothing and Acer website is of little to no help. Hopefully someone here can help me out. 

**P.S. If it helps I am writing this new post using the latest Ubuntu distro on a flash drive and I am having the same issues. **

---

