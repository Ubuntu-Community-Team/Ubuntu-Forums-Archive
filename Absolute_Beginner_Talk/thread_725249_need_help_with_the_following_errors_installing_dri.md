---
title: "need help with the following errors installing driver"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2008-03-15
ok I just finished building my New computer ( first timer ) so I installed unbuntu Gutsy Gibon 64 bit and downloaded  the drivers for my HD 3870 but when I followed the directions at this site  I recieve the following errors which are not covered at the web site
```
dpkg: error processing xorg-driver-fglrx_8.471-0*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.471-0*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.471-0*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.471-0*.deb
 fglrx-kernel-source_8.471-0*.deb
 fglrx-amdcccle_8.471-0*.deb

``` I am pretty new to Linux and at a loss to what that is. Am I missing those files and need to install them?

---

### Post by taurus on 2008-03-15
Are you sure you in the right directory where the ATI driver is?  Perhaps you downloaded it to ~/Desktop so you need to change to that directory first before you can install/run it.

```
cd ~/Desktop
sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb
```

---

### Post by Shadowmeph on 2008-03-15
> **taurus said:**
> Are you sure you in the right directory where the ATI driver is?  Perhaps you downloaded it to ~/Desktop so you need to change to that directory first before you can install/run it.

```
cd ~/Desktop
sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb
```

ooops lol ok that is true I totally for got to change the dir to desktop but now I get these errors
```
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not installed.
 fglrx-amdcccle depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xorg-driver-fglrx_8.471-0ubuntu1_amd64.deb
 fglrx-amdcccle

```

---

