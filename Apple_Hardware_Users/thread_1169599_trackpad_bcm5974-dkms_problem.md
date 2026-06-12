---
title: "trackpad bcm5974-dkms problem"
date: 2009-05-25
forum: Apple Hardware Users
---

### Post by mfleming on 2009-05-25
Folks,

I'd really appreciate your help with the following. I have a MacBook Pro 5.2 with Ubuntu 9.04 installed. I'm trying to follow the instructions from this page [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Touchpad](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Touchpad) to get the touchpad working properly. But when I try to insall bcm5974-dkms I get the following errors:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main dkms 2.0.21.1-0ubuntu3 [57.6kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main usbhid-dkms 0.11.2 [45.0kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main fakeroot 1.12.1ubuntu1 [115kB]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main bcm5974-dkms 1.1.3-0ubuntu1~mactel-support1~intrepid1 [11.2kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main patch 2.5.9-5 [100kB]
Fetched 329kB in 0s (385kB/s) 
Selecting previously deselected package dkms.
(Reading database ... 102008 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.0.21.1-0ubuntu3_all.deb) ...
Selecting previously deselected package usbhid-dkms.
Unpacking usbhid-dkms (from .../usbhid-dkms_0.11.2_all.deb) ...
Selecting previously deselected package bcm5974-dkms.
Unpacking bcm5974-dkms (from .../bcm5974-dkms_1.1.3-0ubuntu1~mactel-support1~intrepid1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.1ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.0.21.1-0ubuntu3) ...
 * Running DKMS auto installation service for kernel 2.6.28-11-generic   [ OK ] 

Setting up usbhid-dkms (0.11.2) ...
Loading new usbhid-0.11.2 DKMS files...

Loading tarball for module: usbhid / version: 0.11.2

Loading /usr/src/usbhid-0.11.2...
Creating /var/lib/dkms/usbhid/0.11.2/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-11-generic -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/var/lib/dkms/usbhid/0.11.2/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.28-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/usbhid/0.11.2/build/ for more information.
0
0
dpkg: error processing usbhid-dkms (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of bcm5974-dkms:
 bcm5974-dkms depends on usbhid-dkms; however:
  Package usbhid-dkms is not configured yet.
dpkg: error processing bcm5974-dkms (--configure):
 dependency problems - leaving unconfigured
Setting up fakeroot (1.12.1ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Setting up patch (2.5.9-5) ...
Errors were encountered while processing:
 usbhid-dkms
bcm5974-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

Help!

---

### Post by cyberdork33 on 2009-05-26
you appear to have your sources setup to retreive the intrepid packages from the PPA, and you are using Jaunty. you need to change them to use the Jaunty packages.

[https://edge.launchpad.net/~mactel-support/+archive/ppa](https://edge.launchpad.net/~mactel-support/+archive/ppa)

---

