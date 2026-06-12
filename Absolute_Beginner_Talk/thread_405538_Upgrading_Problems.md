---
title: "Upgrading Problems"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by peterscj on 2007-04-09
I was trying to upgrade from breezy to edgy by changing the sources.list file but I seem to be getting some errors.  It fails on the dist-upgrade and then tells me to do a apt-get -f install but I just get more errors.  Below is what it shows.  Any ideas?  I don't really want to reinstall the whole thing :(


root@Server1:/sbin# sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  volumeid
The following NEW packages will be installed:
  volumeid
0 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 0B/61.5kB of archives.
After unpacking 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 12263 files and directories currently installed.)
Unpacking volumeid (from .../volumeid_093-0ubuntu18.0edgy2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/volumeid_093-0ubuntu18.0edgy2_i386.deb (--unpack):
 trying to overwrite `/sbin/vol_id', which is also in package udev
Errors were encountered while processing:
 /var/cache/apt/archives/volumeid_093-0ubuntu18.0edgy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Maestro23 on 2007-04-09
According to this doc, you can only upgrade to Edgy from Dapper.

Edgy Upgrade: [https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29](https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29)

---

### Post by peterscj on 2007-04-09
Ah, ok...  

Thanks!  I'll try upgrading to dapper and then to edgy and see if that'll work.

Thanks again :D

---

