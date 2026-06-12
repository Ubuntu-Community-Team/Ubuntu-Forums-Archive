---
title: "can't install evolution, i get the following error."
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by bratliff on 2008-04-10
E: /var/cache/apt/archives/liblaunchpad-integration1_0.1.18_i386.deb: trying to overwrite `/usr/share/icons/hicolor/16x16/apps/lpi-bug.png', which is also in package liblaunchpad-integration0

Using Ubuntu 8.04b. Evolution was working then after an update/

bratliff

---

### Post by buried on 2008-04-10
hmm, try giving it overwrite (yes) settings.

---

### Post by bratliff on 2008-04-10
and when I do the apt-get -f install to fix the dependencies I get this:

root@bob-desktop:/home/bob# apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  imlib11 libnfsidmap2 libevent1 linux-libc-dev
  linux-headers-2.6.24-12-generic librpcsecgss3 imlib-base nfs-kernel-server
  libgssglue1 portmap nfs-common linux-headers-2.6.24-12
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  liblaunchpad-integration1
The following NEW packages will be installed:
  liblaunchpad-integration1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/17.7kB of archives.
After this operation, 172kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158976 files and directories currently installed.)
Unpacking liblaunchpad-integration1 (from .../liblaunchpad-integration1_0.1.18_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/liblaunchpad-integration1_0.1.18_i386.deb (--unpack):
 trying to overwrite `/usr/share/icons/hicolor/16x16/apps/lpi-bug.png', which is also in package liblaunchpad-integration0
Errors were encountered while processing:
 /var/cache/apt/archives/liblaunchpad-integration1_0.1.18_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Bratliff


> **buried said:**
> hmm, try giving it overwrite (yes) settings.

---

### Post by TeoBigusGeekus on 2008-04-10
[http://ubuntuforums.org/showthread.php?t=749400&highlight=broken+package]("http://ubuntuforums.org/showthread.php?t=749400&highlight=broken+package")

---

