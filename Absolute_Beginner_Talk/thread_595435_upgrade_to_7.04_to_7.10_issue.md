---
title: "upgrade to 7.04 to 7.10 issue"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Rex72 on 2007-10-28
I have installed all the latest updates for 7.04 yet when I try to upgrade via network Update Manage I get the following missing items and then it kicks me out.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

What must I do to fix this in order to complete the install?

Thank y ou

---

### Post by overdrank on 2007-10-28
> **Rex72 said:**
> I have installed all the latest updates for 7.04 yet when I try to upgrade via network Update Manage I get the following missing items and then it kicks me out.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

What must I do to fix this in order to complete the install?

Thank y ou

 Hi and welcome, I would recommend check and make sure all your repos are enabled. System, administration, software sources. Then run these commands in the terminal
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist upgrade
```
Hope this helps good luck!

---

