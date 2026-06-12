---
title: "E: Unable to locate package nvidia-bl-dkms"
date: 2014-07-03
forum: Apple Hardware Users
---

### Post by mdmosley1 on 2014-07-03
Hi,

I have an intel mac and I am running ubuntu 14.04. I need to install nvidia-bl-dmks so that I can change the brightness.  I added the mactel-support repo per the instructions here: [https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid). However, when I run sudo apt-get update, I get 

[HTML]
W: Failed to fetch http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
[/HTML]

And when I run apt-get install nvidia-bl-dmks, I get the following error:

[HTML]
E: Unable to locate package nvidia-bl-dkms
[/HTML]
  
I have also tried obtaining nvidia-bl-dmks from here: [http://www.ubuntuupdates.org/package/mactel_support/lucid/main/base/nvidia-bl-dkms](http://www.ubuntuupdates.org/package/mactel_support/lucid/main/base/nvidia-bl-dkms)
But when I try to install it through the software center, I also get errors, which are included in the text file.

Can someone tell me how best to resolve this?

UPDATE:

I realized that I had the trusty distribution selected instead of lucid. I am now able to get the package through apt-get but it still wont build. The terminal returns the following:

```

Unpacking nvidia-bl-dkms (0.17.3~lucid) ...
Setting up nvidia-bl-dkms (0.17.3~lucid) ...
Loading new nvidia_bl-0.17.3 DKMS files...

Loading tarball for nvidia_bl-0.17.3

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/nvidia_bl/0.17.3/source ->
                 /usr/src/nvidia_bl-0.17.3

DKMS: add completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.13.0-30-generic -C /lib/modules/3.13.0-30-generic/build SUBDIRS=/var/lib/dkms/nvidia_bl/0.17.3/build modules....(bad exit status: 2)
ERROR (dkms apport): binary package for nvidia_bl: 0.17.3 not found
Error! Bad return status for module build on kernel: 3.13.0-30-generic (x86_64)
Consult /var/lib/dkms/nvidia_bl/0.17.3/build/make.log for more information.
dpkg: error processing package nvidia-bl-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 nvidia-bl-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So it looks like it's not finding a file. Can someone tell me where I can download an older version of nvidia-bl-dkms that installs properly?

---

### Post by ibjsb4 on 2014-07-03
> I have an intel mac and I am running ubuntu 14.04. I need to install  nvidia-bl-dmks so that I can change the brightness.  I added the  mactel-support repo per the instructions here: [https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid). However, when I run sudo apt-get update, I get 
W: Failed to fetch [http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found 
 W: Failed to fetch [http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
Looks like this ppa is no longer maintained; there is no trusty support.
[http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/)

---

### Post by MikeBraxner on 2014-07-04
While there is no trusty versioning, you might want to try the raring one ... it should install and work without problems.

---

