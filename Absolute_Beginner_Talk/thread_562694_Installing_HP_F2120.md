---
title: "Installing HP F2120"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2007-09-29
I am trying to install a HP F2120 in Xubuntu. The list of supported printers says that the F2000 series requires at least HPLP 1.7.4 but my distro only has 1.7.3. so I downloaded the latest HPLIP and when I run, first of all I get asked if Ubuntu 7.10 is my installation to which I answer yes and then after a while I getthe following error messages:

"INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 6 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: libpthread (libpthread - POSIX threads lib
rary)
warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common Unix Printi
ng System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building suppor
t services)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 7 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto                      - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (lib                     netsnmp-devel - SNMP networking library development files)
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PD                     F library for Python)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scann                     ing library development files)
warning: Missing OPTIONAL dependency for option 'scan': pil (PIL - Python Imagin                     g Library (required for commandline scanning with hp-scan))
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - S                     hell scanning program)
warning: Missing OPTIONAL dependency for option 'scan': xsane (xsane - Graphical                      scanner frontend for SANE)


CHECKING FOR NETWORK CONNECTION
-------------------------------
error:
The network appears to be unreachable. Installation cannot complete without acce                     ss to
error: distribution repositories. Please check the network and try again."


However, the network connection is fine, so what could be going wrong?

---

### Post by Daveth on 2007-09-29
this points out the code needed to apt-get these from the repositories

[http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html)

Make sure you have the main ones in System/admin/software sources/ checked on the front page. I assume you meant the F2100 series, rather than the F2000- though they all point to the same place, so who cares! Hope this works.

---

### Post by tonymoloney on 2007-09-29
Thanks Daveth
Before I got your reply, I managed to get the printer installed by running sudo hp-setup and when I got to the point where it said it couldn't find my printer, I choose to find it manually and used the recommended D2300 driver, which worked.

---

