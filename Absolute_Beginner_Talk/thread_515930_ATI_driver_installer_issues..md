---
title: "ATI driver installer issues."
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by l337a on 2007-08-02
I have a radeon 9200 PRO graphics card that i want to work under ubuntu 7.04. I chmodded everything correctly, and ran it as sudo sh '/home/tyler/Desktop/ati-driver-installer-8.19.10-i386.run'


It gave me this crap: 

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.19.10.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 90: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


I found a solution a while back. It had something to do with moving or renaming a bash or shell directory. I dont know what to do here. =/


And another thing, It says that i don't need any restricted drivers.


ALRIGHT. I found a way to do this. Found it on some shifty mexican site. Now I might bleed out the ***.

so that you of the problem of bas substitution you do not have to do the following thing:
rm /bin/sh
ln - s /bin/bash /bin/sh
later beams sh ati-*.run
and you it would already have to appear the installer.
Greetings.

Now I have... 

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.2.0

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x410        XFree86 4.1.x
    x420        XFree86 4.2.x
    x430        XFree86 4.3.x
    x680        X.Org 6.8.x
    x690        X.Org 6.9.x
Removing temporary directory: fglrx-install

---

### Post by asmoore82 on 2007-08-02
:lolflag: @ ATI ....

can you use "System -> Administration -> Restricted Drivers"
and enable ATI in there?

that's all I did and UT2004 runs great.

---

### Post by l337a on 2007-08-02
Tried that, Says that I don't need any restricted drivers. I think I need them, OpenGL and X runs slowly if I don't have them =/

---

### Post by asmoore82 on 2007-08-02
> **l337a said:**
> Tried that, Says that I don't need any restricted drivers. 

strange, but you should still be able to install them via Synaptic/APT ...

search for "xorg-driver-fglrx" ..

but:
> This version of the ATI driver officially supports:

 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400,
           V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
           X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration)
 * Mobility FireGL: V5000, T2
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300,
                    9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550,
           X300, 9800, 9700, 9600, 9550, 9500

doesn't say anything about 9200; that might be the problem ](*,)

---

### Post by l337a on 2007-08-02
I should of also mentioned that I do have a 9200. It was a cheap-o card. ^^;

But It runs half-life 2 at about 60fps :D

---

### Post by asmoore82 on 2007-08-02
i would still try installing fglrx in Synaptic ...
what's the worst thing that could happen:evil:?

---

### Post by l337a on 2007-08-02
I already tried doing that, It has no effect whats so ever. Infact, come to think of it...

It made things slower than they were with the open driver :|

---

