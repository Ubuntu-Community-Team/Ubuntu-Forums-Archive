---
title: "BootX, 6.10, OldWorldMac- Not Booting"
date: 2007-02-24
forum: Apple PPC Users
---

### Post by mdknaebel on 2007-02-24
I am trying to install Ubuntu 6.10 on an old world Mac using BootX and the alternate installation CD.  I am able to run the first part of the installation from the CD, but once it goes on to install from the hard drive, it will not boot back into the installation.  I have tried to follow this guide: [http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/](http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/)
although it is for Ubuntu 5.10.

When I boot back up, I put in the kernel arguments, however it stops part-way through the boot process.  A few of the 'OK's' come up and then it freezes at "*Running local boot scripts".  It allows me to login, but there is no GUI.

In the kernel arguments I typed: "root=/dev/hda12" Hda 12 is my ext3 partition. should I instead point it to my ext2?

I am kind of new to Linux but I would appreciate any help

Thanks

---

