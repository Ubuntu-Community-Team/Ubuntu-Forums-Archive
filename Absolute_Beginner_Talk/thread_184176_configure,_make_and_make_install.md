---
title: "configure, make and make install"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-05-29
Hi

When I configure I get this error:

configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!

How do I fix it please?

---

### Post by mostwanted on 2006-05-29
Install what it says you're missing (can usually be found in the repos). You usually need the packages suffixed with -dev.

---

### Post by mrvgarg on 2006-05-29
I did aptitude install libjpeg and Qt but I still get the errors when i do ./configure

---

### Post by az on 2006-05-29
[QUOTE=mrvgarg]I did aptitude install libjpeg and Qt but I still get the errors when i do ./configure[/QUOTE]
You would need the libqt4-mt-dev packages or something like that.  What are you trying to compile?  Read the README which describes the requirements for building (it will tell you it needs the qt libraries and so forth.  They are packaged with the -dev suffix.  You need to install them.)

---

### Post by mrvgarg on 2006-05-29
I am trying to install koverartist

---

### Post by mrvgarg on 2006-05-29
i got of the libjpeg error but the qt error is still there. I tried

./configure --with-qt-dir=/usr/lib/qt3

but it still wont work.

---

### Post by az on 2006-05-29
[QUOTE=mrvgarg]I am trying to install koverartist[/QUOTE]

You need  a newer version than what's in the repos?

apt-cache show koverartist
Package: koverartist
Priority: optional
Section: universe/kde
Installed-Size: 504
Maintainer: Jonathan Patrick Davies <jpatrick@ubuntu.com>
Architecture: i386
Version: 0.3.2-0ubuntu1
Depends: kdelibs4c2a (>= 4:3.5.2), libacl1 (>= 2.2.11-1), libart-2.0-2 (>= 2.3.16), libattr1 (>= 2.4.4-1), libaudio2, libc6 (>= 2.3.4-1), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.10-1), libgamin0, libgcc1 (>= 1:4.0.2), libice6, libidn11 (>= 0.5.18), libjpeg62, libpng12-0 (>= 1.2.8rel), libqt3-mt (>= 3:3.3.6), libsm6, libstdc++6 (>= 4.0.2-4), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, zlib1g (>= 1:1.2.1)
Filename: pool/universe/k/koverartist/koverartist_0.3.2-0ubuntu1_i386.deb
Size: 129860
MD5sum: dc1ac7c608f79a0a4ad543f4d56ef80b
Description: program for the fast creation of covers for CD/DVD cases and boxes
 The main idea behind KoverArtist is to be able to create decent looking covers
 with some mouseclicks.
 .
 Homepage: [http://kde-apps.org/content/show.php?content=38195](http://kde-apps.org/content/show.php?content=38195)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

