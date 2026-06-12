---
title: "Trouble with NetBoot install on iMac G3"
date: 2007-01-07
forum: Apple PPC Users
---

### Post by poopdeville on 2007-01-07
Hi everybody,

I'm having some trouble installing Edgy on my G3 iMac (500 Mhz, 256 MB of ram, I think).  My iMac's slot loading drive is broken, and a replacement is very expensive.  So I tried running the netboot installer ([http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current//images/powerpc/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current//images/powerpc/netboot/mini.iso)) but I've run into some difficulties.

First, I must say that the netboot installer has several annoying bugs in the yaboot.conf file.  (All the paths of the form /install/blah should be of the form install/blah) And it doesn't include any documentation, which made figuring that first part out an exercise in repetitive experimentation.  Where should I file a bug report about that?

Second, and this is the big problem:  I get yaboot to load, select the kernel I want, and end up with this error:

Transfer FILE: install/netboot-initrd.gz method 'load' failed 00000300 ramdisk load failed !

I did some research and eventually found out that this error means that the ramdisk is too big for OpenFirmware to deal with.

So, I would like some help.  I've used the Debian version of 'mini.iso' to installed Debian on this machine before.  But I would like Ubuntu installed.  How would I go about fixing Ubuntu's ramdisk issue?  Is filing a bug report the best I can do?  Or, better yet, how could I use Debian's mini.iso to install Ubuntu?

Any help would be appreciated.  Thank you!

---

