---
title: "GnuCash &amp; Feisty Fawn"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-05-12
I recently upgraded to 7.04 and had to uninstall GnuCash to make space. I am now having trouble reinstalling it. The error message tells me the application conflicts with other installed software without saying what that might be. Help would be appreciated, Thanks.

---

### Post by Najand on 2007-05-12
Copy and paste the error message here and we will help you!

---

### Post by linuxforrealpeople on 2007-05-12
[IMG]http://i98.photobucket.com/albums/l258/Hailogon/GNUErrorMessage.jpg[/IMG]

Here you go.

---

### Post by euler_fan on 2007-05-12
I hate to state the obvious, but if you try Synaptic then is should tell you what packages are in conflict and give you the option to resolve the conflicts.

In Gnome it us under System->Administration->Synaptic Package Manager.

---

### Post by Najand on 2007-05-12
It is a Universe Package.
Have you enabled universe/multiverse repositories? (If not,
do it at: System -> Administration -> Software Sources)
And check the all boxes at "ubuntu software"
Reference:

> Package: gnucash
Priority: extra
Section: universe/gnome
Installed-Size: 6512
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Thomas Bushnell, BSG <tb@debian.org>
Architecture: i386
Version: 2.0.2-3ubuntu1
Replaces: gnucash-common (<< 1.9.8-1)
Depends: gnucash-common (>= 2.0.2-3ubuntu1), guile-1.6-libs, libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.3.12), libffi4 (>= 4.1.1-21ubuntu1), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomeprint2.2-0 (>= 2.17.0), libgnomeprintui2.2-0 (>= 2.17.0), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 2.17.90), libgsf-1-114 (>= 1.14.3), libgsf-gnome-1-114 (>= 1.14.3), libgtk2.0-0 (>= 2.10.3), libgtkhtml3.8-15 (>= 3.13.6), libguile-ltdl-1, libgwrap-runtime0 (>= 1.9.4-3), libice6 (>= 1:1.0.0), libltdl3 (>= 1.5.2-2), libofx3, liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.15.5), libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.10), libqthreads-12, libsm6, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2, libxrender1, zlib1g (>= 1:1.2.1), gconf2 (>= 2.12.1-4ubuntu1), slib (>= 3a2-5), guile-1.6-slib, libfinance-quote-perl, libdate-manip-perl, psfontmgr, x-ttcidfont-conf, g-wrap, guile-g-wrap, libcrypt-ssleay-perl
Suggests: gnucash-sql, gnucash-docs
Filename: pool/universe/g/gnucash/gnucash_2.0.2-3ubuntu1_i386.deb
Size: 2114578
MD5sum: c65f34203203b4e501b045557d805e66
SHA1: 2466175278d78b2cde1c3c5ca27a6fb1cda3bd0f
SHA256: 53cb885c8e81bd710631b7bdd5e57f4aa8126af21217bed9c101023c9c8ac6c4
Description: A personal finance tracking program
 Gnucash can track finances in multiple accounts, keeping running
 and reconciled balances. It has an X based graphical user interface,
 double entry, a hierarchy of accounts, expense accounts (categories),
 and can import Quicken QIF files and OFX files.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by linuxforrealpeople on 2007-05-12
> **euler_fan said:**
> I hate to state the obvious, but if you try Synaptic then is should tell you what packages are in conflict and give you the option to resolve the conflicts.

In Gnome it us under System->Administration->Synaptic Package Manager.
The obvious is always the best place to start. That all worked very nicely thanks. This is my first use of synaptic to do an install so that explains my obtuseness.

---

