---
title: "Ubuntu with ACX111 based wireless card"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by bluedevil on 2006-08-26
I have done extensive online research on getting my wireless card up and running with Ubuntu Dapper Drake. On the basis of this research, I've tried a lot of things. However, as a Linux newbie most of the advice assumes significantly more Linux knowledge than I have and the card is still not working.

Here's my situation:

- I have a Netgear WG311v2 wireless card based on the ACX111 chipset.

- After my initial Ubuntu install a few days ago wireless didn't work at all.

- I downloaded a driver from sourceforge and used the commands:
1. sudo apt-get install build-essential linux-headers-`uname -r`
2. make -C /lib/modules/`uname -r`/build M=`pwd`
3. sudo make -C /lib/modules/`uname -r`/build M=`pwd` modules_install

- This didn't work initially because I needed to install gcc and a couple of other things. I did that and got make working. When I ran it I got the following message:
make: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'

- This seemed to work, but the wireless card still wasn't working.

- On the Wiki for the driver it said to unload any current modules with:
lsmod | grep acx
That will list any modules with 'acx' in the name. Watch for acx or acx_pci or acx_usb
modprobe -r <module name> will unload a module

- I did that and then did the test the Wiki recommended which was to use the command: insmod ./acx.ko This command gave me a no such file error.

- I also saw there is a bug with the firmware for this chipset and ubuntu. However, I don't know how firmware works in Linux so I don't know what to do about it.

Basically, I'm stuck at this point. I'm just learning Linux now so I tried these things without really understanding how they work. I'm trying to learn my way through this, but any help would be appreciated.

Thanks in advance!

---

