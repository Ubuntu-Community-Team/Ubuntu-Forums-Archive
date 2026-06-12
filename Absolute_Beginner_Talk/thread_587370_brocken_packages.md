---
title: "brocken_packages"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by sn0m on 2007-10-22
Trying to fix broken packages, cannot seem to get through.
I'd appreciate if someone could have a look and help me out.

sn0m@sn0m-laptop:~$ sudo apt-get install -f
[sudo] password for sn0m:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  openoffice.org-core
Recommended packages:
  nfs-common
The following packages will be upgraded:
  openoffice.org-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0B/37.2MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 96214 files and directories currently installed.)
Preparing to replace openoffice.org-core 1:2.3.0-1ubuntu5 (using .../openoffice.org-core_1%3a2.3.0-1ubuntu5.1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libsvt680li.so')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
sn0m@sn0m-laptop:~$ 

Ta
Koli

---

### Post by Beggar on 2007-10-22
Not an expert, did find this though

[http://osdir.com/ml/org.user-groups.linux.vlug/2005-03/msg00412.html](http://osdir.com/ml/org.user-groups.linux.vlug/2005-03/msg00412.html)

---

