---
title: "Upgrade from ubuntu 7.04 to 7.10 fails for me"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by ycsunil on 2007-10-23
Today I tried to upgrade my ubuntu 7.04 to 7.10 and ended with an error saying: "error during update, A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry."  The packages were Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

---

### Post by shae on 2007-10-23
The servers are probably a little busy with the initial wave of upgrades still.  Be patient or try a local mirror.

---

### Post by JBAlaska on 2007-10-23
You need to open software sources, third party tab and uncheck all repo's pointing to feisty.

---

