---
title: "Detected version of X does not have a matching 'x130' directory"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by SovereignThinker on 2007-12-31
joshua@A55H01E:~/Desktop$ bash ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 1.3.0

Detected version of X does not have a matching 'x130' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        Unknown X Window
    x710_64a    Unknown X Window
Removing temporary directory: fglrx-install

When I use the basic drivers suggested by ubuntu, I get black screen of death on both onboard and ati card. Furthermore, my graphics setup is showing three cards (I only have two), and three screen options, which I only have one monitor with two possible ports.

My monitor is a dell e156fp, and my on board is an intel 865. I really don't want to use it, although it is what I am currently using...

---

### Post by blueridgedog on 2008-01-01
Rather than installing the ATI binary, try installing the deb package:

After enabling the restricted repository follow method one here:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

