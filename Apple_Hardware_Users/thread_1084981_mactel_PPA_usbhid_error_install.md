---
title: "mactel PPA usbhid error install"
date: 2009-03-02
forum: Apple Hardware Users
---

### Post by inphektion on 2009-03-02
I'm on MacBookPro5,2 with latest jaunty.  Added mactel PPA from intrepid and when installing usbhid-dkms I get this:
```

root@nihility:~# aptitude install usbhid-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  usbhid-dkms 
0 packages upgraded, 1 newly installed, 0 to remove and 31 not upgraded.
Need to get 0B/45.0kB of archives. After unpacking 73.7kB will be used.
Writing extended state information... Done
Selecting previously deselected package usbhid-dkms.
(Reading database ... 104346 files and directories currently installed.)
Unpacking usbhid-dkms (from .../usbhid-dkms_0.11.2_all.deb) ...
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
make KERNELRELEASE=2.6.28-8-generic -C /lib/modules/2.6.28-8-generic/build SUBDIRS=/var/lib/dkms/usbhid/0.11.2/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.28-8-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/usbhid/0.11.2/build/ for more information.
0
0
dpkg: error processing usbhid-dkms (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 usbhid-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up usbhid-dkms (0.11.2) ...
Removing old usbhid-0.11.2 DKMS files...

------------------------------
Deleting module version: 0.11.2
completely from the DKMS tree.
------------------------------
Done.
Loading new usbhid-0.11.2 DKMS files...

Error! Cannot locate /usr/src/usbhid-0.11.2.dkms.tar.gz.
File does not exist.
dpkg: error processing usbhid-dkms (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 usbhid-dkms
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done


```

Was this just not made for the jaunty kernel yet? or the 64bit throwing it?

---

### Post by cyberdork33 on 2009-03-02
> **inphektion said:**
> Was this just not made for the jaunty kernel yet? 
That's correct, that's why the packages are accessible for Intrepid and not Jaunty.

---

### Post by lambengolmor on 2009-04-30
So? we just wait?

---

