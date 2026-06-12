---
title: "digikam upgrade and libgphoto2 &gt;= 2.3.1.3.trunk not met"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by weedwacker on 2007-09-11
Hi, all!

I an running Feisty Fawn and I have digiKam installed and would like to use it  with my new camera HP Photosmart R967.

After some experimentation I found that I need a newer version of the PTP2 driver contained in the **gphoto** file: libgphoto2 2.4.0.

I downloaded libgphoto2 2.4.0 from Sourceforge, but before I did the "./configure, make, make install" dance I installed the **build-essential **package from Synaptic.

When I typed in the terminal: **cd gphoto** to get to the directory and then typed: ./configure I got this at the very end:

[INDENT]checking for libgphoto2 to use... autodetect
checking for LIBGPHOTO2... no
checking libgphoto2 config program... gphoto2-config
checking for gphoto2-config... /usr/bin/gphoto2-config
checking for libgphoto2 version according to gphoto2-config... 2.3.0
checking if libgphoto2 version is matching requirement >= 2.3.1.3.trunk... no
configure: error: Version requirement libgphoto2 >= 2.3.1.3.trunk not met. Found: 2.3.0
my@mine-desktop:~/gphoto$ [/INDENT]

I was a bit leery about installing a file libgphoto2 2.3.1.3 because some were referenced to SUSE and others.  Not Ubuntu.

Would you recommend that I wait until the new version of Ubuntu comes out in October to see if my required driver is included for my hp R967?

---

