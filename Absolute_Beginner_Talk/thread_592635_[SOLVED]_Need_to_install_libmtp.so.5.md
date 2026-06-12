---
title: "[SOLVED] Need to install libmtp.so.5"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by orbital on 2007-10-26
I need to install libmtp.so.5 (for Gnomad2) but when I try to install it with apt-get I get the following error:

```

Package libmtp5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmtp5 has no installation candidate

```

How do I install this package?

---

### Post by FredB on 2007-10-26
Which Ubuntu release are you using ?

What does aptitude show libmtp5 say ?

Under Gutsy - and libmtp6, I got :

```
~$ aptitude show libmtp6
Paquet : libmtp6
État: installé
Automatiquement installé: oui
Version : 0.2.1-0ubuntu3
Priorité : optionnel
Section : libs
Responsable : Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Taille décompressée : 352k
Dépend: udev, libc6 (>= 2.6-1), libusb-0.1-4 (>= 2:0.1.12)
Est en conflit: libmtp-dev (< 0.1.3-0ubuntu1), libmtp5
Remplace: libmtp-dev (< 0.1.3-0ubuntu1)
Description : Media Transfer Protocol (MTP) library
 A library for communicating with MTP aware devices.  MTP (Media Transfer
 Protocol) is necessary to communicate with some USB portable devices like mp3
 players, video players or digital camera. 
 
 While some portable device will use USB mass storage protocol or PTP (picture
 transfer protocol), some device can only communicate through MTP [ see
 http://en.wikipedia.org/wiki/Media_Transfer_Protocol ] 
 
 Homepage: http://libmtp.sourceforge.net/
```

---

### Post by orbital on 2007-10-26
> **FredB said:**
> Which Ubuntu release are you using ?

What does aptitude show libmtp5 say ?

Under Gutsy - and libmtp6, I got :

```
~$ aptitude show libmtp6
Paquet : libmtp6
État: installé
Automatiquement installé: oui
Version : 0.2.1-0ubuntu3
Priorité : optionnel
Section : libs
Responsable : Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Taille décompressée : 352k
Dépend: udev, libc6 (>= 2.6-1), libusb-0.1-4 (>= 2:0.1.12)
Est en conflit: libmtp-dev (< 0.1.3-0ubuntu1), libmtp5
Remplace: libmtp-dev (< 0.1.3-0ubuntu1)
Description : Media Transfer Protocol (MTP) library
 A library for communicating with MTP aware devices.  MTP (Media Transfer
 Protocol) is necessary to communicate with some USB portable devices like mp3
 players, video players or digital camera. 
 
 While some portable device will use USB mass storage protocol or PTP (picture
 transfer protocol), some device can only communicate through MTP [ see
 http://en.wikipedia.org/wiki/Media_Transfer_Protocol ] 
 
 Homepage: http://libmtp.sourceforge.net/
```

I'm running Gutsy and aptitude show libmtp5 gives me:

```

No current or candidate version found for libmtp5
Package: libmtp5
State: not installed
Version: 0.1.3-0ubuntu2
Priority: optional
Section: libs
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 319k
Depends: udev, libc6 (>= 2.5-0ubuntu1), libusb-0.1-4 (>= 2:0.1.12)
Conflicts: libmtp-dev (< 0.1.3-0ubuntu1), libmtp2
Replaces: libmtp-dev (< 0.1.3-0ubuntu1)
Description: Implementation of Microsoft's MTP
 libmtp is a implementation of Microsoft's Media Transfer Protocol (MTP) in the
 form of a library suitable primarily for POSIX compliant operating systems. We
 implement MTP Basic, the stuff proposed for standardization. 
 
 Homepage: http://libmtp.sourceforge.net/

```

The problem is when I try to run Gnomad2 I get this error:

```

gnomad2: error while loading shared libraries: libmtp.so.5: cannot open shared object file: No such file or directory

```

Gnomad2 worked well before I upgraded to Gutsy. After upgrade it hasn't worked.

---

### Post by orbital on 2007-10-31
Installed Gnomad2 from source and it works.

---

