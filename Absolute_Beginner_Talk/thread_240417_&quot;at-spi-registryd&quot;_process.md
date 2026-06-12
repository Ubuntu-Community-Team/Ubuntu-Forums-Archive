---
title: "&quot;at-spi-registryd&quot; process?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by bhoughton on 2006-08-20
Like to check System Monitor from time to time and tonight noticed a process named "at-spi-registryd" that I hadn't noticed before (been about a week since looking at the monitor).  Does anyone have an idea as to what it is?

---

### Post by pollock.tar.gz on 2006-08-20
im not so sure what it is..but i probably wouldnt worry about it.

---

### Post by jobezone on 2006-08-20
> **bhoughton said:**
> Like to check System Monitor from time to time and tonight noticed a process named "at-spi-registryd" that I hadn't noticed before (been about a week since looking at the monitor).  Does anyone have an idea as to what it is?

$dpkg -S at-spi-registryd

at-spi: /usr/lib/at-spi/at-spi-registryd

$ apt-cache show at-spi

Package: at-spi
Priority: optional
Section: gnome
Installed-Size: 1384
Maintainer: Akira TAGOH <tagoh@debian.org>
Architecture: i386
Version: 1.7.7-0ubuntu3
Replaces: libatspi-dev (<< 1.6.0-2)
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libatspi1.0-0 (>= 1.7.7), libbonobo2-0 (>= 2.13.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.10-1), libgail-common (>= 1.6.6), libgail17 (>= 1.6.6), libglib2.0-0 (>= 2.10.0), libgnomecanvas2-0 (>= 2.11.1), libgtk2.0-0 (>= 2.8.0), libice6, liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.12.2), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libsm6, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxtst6, zlib1g (>= 1:1.2.1)
Filename: pool/main/a/at-spi/at-spi_1.7.7-0ubuntu3_i386.deb
Size: 183112
MD5sum: 258d8e255d97a0a24838f619f4255982
Description: Assistive Technology Service Provider Interface
 Providing accessibility means removing barriers that prevent people
 with disabilities from participating in substantial life activities,
 including the use of services, products, and information.
 Assistive access means that system infrastructure allows add-on
 assistive software to transparently provide specialized input and
 output capabilities.
 .
 This package contains the core components of GNOME Accessibility.
 if you need to use Assistive technology, install it.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop

Something to do with acessibility in gnome.

---

### Post by bhoughton on 2006-08-20
Thanks for the info.  Just wanted to check it out.

Regards...

---

