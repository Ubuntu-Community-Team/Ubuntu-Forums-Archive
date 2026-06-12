---
title: "Trying to set up file sharing on VMWare"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by hojjat on 2008-01-09
I'm trying to set up file sharing on VMWare (as described [here]("http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/")), but I get an error message while trying to build "vmhgfs" for my machine, as pasted below:

```

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmhgfs-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/dev.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/driver.o
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsChangeFileAttributes’:
/tmp/vmware-config0/vmhgfs-only/driver.c:763: error: ‘struct inode’ has no member named ‘i_blksize’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsInitializeInode’:
/tmp/vmware-config0/vmhgfs-only/driver.c:835: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsIget’:
/tmp/vmware-config0/vmhgfs-only/driver.c:884: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsCreate’:
/tmp/vmware-config0/vmhgfs-only/driver.c:1536: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsLookup’:
/tmp/vmware-config0/vmhgfs-only/driver.c:1636: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsMkdir’:
/tmp/vmware-config0/vmhgfs-only/driver.c:1728: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsDelete’:
/tmp/vmware-config0/vmhgfs-only/driver.c:1855: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsRename’:
/tmp/vmware-config0/vmhgfs-only/driver.c:2048: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c:2050: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsRevalidate’:
/tmp/vmware-config0/vmhgfs-only/driver.c:2294: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsSetattr’:
/tmp/vmware-config0/vmhgfs-only/driver.c:2431: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsOpen’:
/tmp/vmware-config0/vmhgfs-only/driver.c:2808: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsDirOpen’:
/tmp/vmware-config0/vmhgfs-only/driver.c:3422: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config0/vmhgfs-only/driver.c: In function ‘HgfsClearInode’:
/tmp/vmware-config0/vmhgfs-only/driver.c:4113: error: ‘struct inode’ has no member named ‘u’
make[2]: *** [/tmp/vmware-config0/vmhgfs-only/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.

```

Please advise what I should do to make it work.

---

### Post by dcstar on 2008-01-09
> **hojjat said:**
> I'm trying to set up file sharing on VMWare (as described [here]("http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/")), but I get an error message while trying to build "vmhgfs" for my machine, as pasted below:
........
Please advise what I should do to make it work.

Firstly, vmware server is available in the Gutsy repositories, so there is no need whatsoever to muck around with outdated instructions that obviously don't work for you.

Secondly, there is a separate Virtualization forum that is meant for these questions:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by hojjat on 2008-01-09
With more investigation (and thanks to [this post]("http://ubuntuforums.org/showthread.php?t=595348")), I found that my kernel version (2.6.20) was not supported with the version of VMWare I had (5.1.2600). Right now, I'm looking for a way to get the newer versin of VMWare tools.

---

### Post by hojjat on 2008-01-09
David. I'm using Feisty and it is not possible for me to upgrade with my dial-up connection.

---

### Post by lgambett on 2008-01-09
Your host operating system is Ubuntu (I guess) and your guest operating system is ...?

---

### Post by hojjat on 2008-01-10
My guest OS is Ubuntu Feisty, my host OS is Windows XP.

---

### Post by hojjat on 2008-01-11
Any idea?

---

### Post by lgambett on 2008-01-12
Apologize for the delay. The answer is very easy; share the folder in Windows, verify that you have installed the smb-client package in Ubuntu, then you can browse the shared folders of the Windows host from the Ubuntu guest.

---

### Post by hojjat on 2008-01-13
That is not what I'm looking for. I'm trying to use VMWare's sharing method ([link]("http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/"), [link]("http://www.howtogeek.com/howto/ubuntu/how-to-share-folders-with-your-ubuntu-virtual-machine-guest/")) and for that, I need to build vmhgfs module. I'm getting that error message, so regardless of the other possible ways of sharing files, what I want to know is why I'm getting that error message.

---

### Post by lgambett on 2008-01-13
Ok, changing community... because this is a VMware issue (not Ubuntu) have a look here:
[http://communities.vmware.com/thread/61418?tstart=0&start=15](http://communities.vmware.com/thread/61418?tstart=0&start=15)
good luck !

---

### Post by hojjat on 2008-01-14
> **lgambett said:**
> Ok, changing community... because this is a VMware issue (not Ubuntu) have a look here:
[http://communities.vmware.com/thread/61418?tstart=0&start=15](http://communities.vmware.com/thread/61418?tstart=0&start=15)
good luck !

Thanks for the recommendation. Anyways, I think not being able to MAKE an executable is rather a Linux question.

---

### Post by lgambett on 2008-01-16
Yes, this is correct. It is a Linux & VMware question; my point was that the error is reported also in Debian and Fedora, thus is not Ubuntu - specific :).
I hope you managed to solve your problem !

---

### Post by hojjat on 2008-01-19
> **lgambett said:**
> Yes, this is correct. It is a Linux & VMware question; my point was that the error is reported also in Debian and Fedora, thus is not Ubuntu - specific :).
I hope you managed to solve your problem !

Unfortunately, I haven't solved it yet. I still hope someone would come and tell me what to do.

---

### Post by hojjat on 2008-01-25
I solved my problem by following the instructions on this page: [http://tuxx-home.at/cmt.php?article=/2007/06/29/T12_33_53/index.html](http://tuxx-home.at/cmt.php?article=/2007/06/29/T12_33_53/index.html)

Thank you for your replies.

---

