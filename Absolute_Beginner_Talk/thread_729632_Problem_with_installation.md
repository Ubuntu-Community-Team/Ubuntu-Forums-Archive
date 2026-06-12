---
title: "Problem with installation"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by npopov on 2008-03-20
```
root@comp:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libopenexr2c2a libpcre3
The following NEW packages will be installed:
  libopenexr2c2a libpcre3
0 upgraded, 2 newly installed, 0 to remove and 186 not upgraded.
23 not fully installed or removed.
Need to get 0B/502kB of archives.
After unpacking 1372kB of additional disk space will be used.
Do you want to continue [Y/n]? y     
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libpcre3_7.4-0ubuntu0.7.04.2_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ... 102127 files and directories currently installed.)
Unpacking libopenexr2c2a (from .../libopenexr2c2a_1.2.2-4.3ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libopenexr2c2a_1.2.2-4.3ubuntu1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg-deb: `/var/cache/apt/archives/libpcre3_7.4-0ubuntu0.7.04.2_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/libpcre3_7.4-0ubuntu0.7.04.2_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libopenexr2c2a_1.2.2-4.3ubuntu1_i386.deb
 /var/cache/apt/archives/libpcre3_7.4-0ubuntu0.7.04.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@comp:~# 

```

Help??

---

### Post by kesman on 2008-03-20
run
```

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

```

---

