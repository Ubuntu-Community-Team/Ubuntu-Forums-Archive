---
title: "Problem with ATi drivers"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by dabbner on 2007-04-19
Be gentle, relative noob here... 

I'm installing the ATI drivers for my 9800 and get the following:

root@Ubuntu-D:/home/alex/Desktop# sudo ./ati-driver-installer-8.36.5-x86.x86_64.run 
Created directory fglrx-install.LF6570
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.36.5...............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.2.x 64-bit

Detected version of X does not have a matching 'x720_64a' directory
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
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.LF6570

I am running 7.04 fresh install using the driver loaded from "restricted drivers manager" but I want to adjust my screen res and enable dual LCD's.  Am I going about this all wrong?  It looks like I need a driver that works with x.org 7.2, but the one I am using is the latest from the ATI site.

advice?

---

### Post by leibowitz on 2007-04-25
> I am running 7.04 fresh install using the driver loaded from "restricted drivers manager"

Why are you trying to install ATI driver if it's already installed.

I know, monitor etc. ok but you can do that without installing again a new ati driver. And manual installation is far more difficult than just checking a box in the restricted drivers manager

---

