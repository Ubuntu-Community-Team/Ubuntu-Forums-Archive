---
title: "A question...before I buy hardware"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by oubaas on 2007-07-01
A little advice will be appreciated.....
Upgrade time has arrived (again), and I am tempted by an online mobo combo deal:

 Intel D945GCCRL Intel Socket MicroATX Motherboard
Intel Core 2 Duo E4300 1.80GHz OEM Processor
Ultra 1024MB PC4200 DDR2 533MHz Memory

When I check the Intel website, it is listed as NOT supporting Linux.
Does this mean they have not tested it, or is it a windoze-only board that is best left well alone?
I run Ubuntu 7.04 i386.

Thanks
Oubaas

---

### Post by Jimmyfj on 2007-07-01
Well if Intel say that the board is not supporting Linux I'd go find another that does - Intel is, normally among those who support Linux quite well, and if they say that a board isn't supported well....

Anyways - I'd at any given time suggest a MSI motherboard with a VIA chipset for any processor available, I have only had great experiences with their boards and VIA chipsets.

---

### Post by Raineer on 2007-07-01
More often than not I find vendors just don't bother to mention Linux for one reason or another.  I have a feeling it would work fine, but maybe there isn't support for some of the advanced features of the board in Linux (like overclocking utilities)

---

### Post by wolfen69 on 2007-07-01
it's nice to have the latest and greatist, but with linux sometimes you have to back off a bit. get a mobo that is a little bit "older", and you should have no problems. i find gigabyte boards to work very well in linux.

---

### Post by logos34 on 2007-07-01
Well, it doesn't look like there are any linux drivers for this board listed on Intel site...Intel is usually pretty good at that (i.e. enterprise Suse, red Hat, etc)...Surprised there are none for this board.  OTH I don't think you will have any problem with the 945G chipset and HD audio in linux, as it should work out of the box with the oss drivers in feisty.  The mobile GM version linux support looks good--[see this]("http://intellinuxgraphics.org/user.html").  For sound you'll probably use the alsa driver intel_hd, and the graphics driver xserver-xorg-video-intel

from 
[COLOR="Blue"]http://intellinuxgraphics.org/download.html[/COLOR]:
> Source Code
Compiling and/or upgrading graphics drivers in Linux is a complex and error-prone task. Here is a user guide for how to build the driver from scratch. If you are not experienced doing this, we recommend that you get precompiled packages from one of the many Linux distributions.

Note: **If you have a 945 or older graphics controller, your distribution will already have the right drivers included.** 

> 
~$ apt-cache search intel video
915resolution - resolution modification tool for Intel graphic chipset
libcv-dev - development files for libcv
libcv0.9.7-0 - computer vision library
libcvaux-dev - development files for libcvaux
libcvaux0.9.7-0 - computer vision extension library
libhighgui-dev - development files for libhighgui
libhighgui0.9.7-0 - computer vision GUI library
opencv-doc - OpenCV documentation and examples
python-opencv - Python bindings for the computer vision library
python2.4-opencv - Python bindings for the computer vision library
xserver-xorg-video-intel - X.Org X server -- Intel i8xx, i9xx display driver
xserver-xorg-video-i740 - X.Org X server -- i740 display driver
xserver-xorg-video-i810 - X.Org X server -- Intel i8xx, i9xx display driver
w32codecs - win32 binary codecs

:~$ apt-cache show xserver-xorg-video-intel
Package: xserver-xorg-video-intel
Priority: optional
Section: universe/x11
Installed-Size: 344
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Version: 1.6.0-0ubuntu1
Replaces: xserver-xorg (<< 6.8.2-35)
Provides: xserver-xorg-video
Depends: libc6 (>= 2.4-1), xserver-xorg-core (>= 1:1.1.1-0ubuntu7), xserver-xorg-video-i810
Filename: pool/universe/x/xserver-xorg-video-intel/xserver-xorg-video-intel_1.6.0-0ubuntu1_i386.deb
Size: 126630
MD5sum: d0d0968b37c0303efcd63d531cc34d44
SHA1: a6d098f7cd0fee6c0a4935d31aa1dee843cc88c0
SHA256: fbc8225f14d8d6259b6c8c0e395f5db2a720dfc4803170bbc833f2b672186dcc
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides an alternative driver for the Intel i8xx and i9xx
 family of chipsets, including i810, i815, i830, i845, i855, i865, i915,
 and** i945** series chips.
 .
 This package also provides an XvMC (XVideo Motion Compensation) driver
 for the same chipsets.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

Buit don't take my word for it.  Google it.

---

### Post by oubaas on 2007-07-02
Thanks to all for your input,
I will buy a setup that is slightly older, and one that I can find drivers for on the manufacturer's website.
I need something that will ideally be able to take a seamless install from a CD, I don't have the skills to be able to tweak an install to match hardware.
Now I'm debating whether I should even bother going with a dual-core CPU.

---

### Post by logos34 on 2007-07-02
Ubuntu has had out-of-box dual-core support for some time now--it's not like you have to compile your own or anything.  It's all done for you during install.  And using manufacturer-supplied linux drivers is not always necessarily better, plus it's actually takes a bit more time and effort (vs. just accepting the default open-source drivers included in Feisty).  I doubt you'll have to tweak anything as long as you avoid bleeding edge (which 945 is not).
But it's always a good idea to do your homework so as to avoid any reported issues with ethernet and sata controllers, etc.

good luck.

---

### Post by cantormath on 2007-07-02
I would get something with a gigabyte linux bios.....

---

