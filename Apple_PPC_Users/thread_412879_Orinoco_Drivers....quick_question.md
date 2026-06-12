---
title: "Orinoco Drivers....quick question"
date: 2007-04-18
forum: Apple PPC Users
---

### Post by gevans on 2007-04-18
I followed the guide at :
[https://help.ubuntu.com/community/WifiDocs/OrinocoKismet?highlight=%28kismet%29](https://help.ubuntu.com/community/WifiDocs/OrinocoKismet?highlight=%28kismet%29)

Got to the part where I type make and this is what happened.

#cd /usr/src/orinoco-0.15
# make
make -C /usr/src/linux-headers-2.6.20-15-powerpc M=/usr/src/orinoco-0.15 KERNELRELEASE=2.6.20-15-powerpc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-powerpc'
/usr/src/orinoco-0.15/Kbuild:38: *** This driver is already enabled in the kernel.  Stop.
make[1]: *** [_module_/usr/src/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-powerpc'
make: *** [modules] Error 2
#

can anyone tell me what I need to do to get this to compile?

Regards,

Greg

---

### Post by gevans on 2007-04-18
So I looked around and was told I needed to rmmod the modules so it would compile. I did this and I get the same error :/

doing an lsmod reveals that the modules are indeed uninstalled. I moved the old orinoco files and the hermes file to a directory that I made in case something broke. 

So, can anyone tell me why this is happening?? maybe I need to post this in the networking section? so I will do that as well.

---

