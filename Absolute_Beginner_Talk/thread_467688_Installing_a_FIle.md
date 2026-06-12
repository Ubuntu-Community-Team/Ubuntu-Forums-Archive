---
title: "Installing a FIle"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Don_Juan on 2007-06-08
WAS HELPED! THANK YOU!

QCA TLS Plugin v1.0
-------------------
Author: Justin Karneges <justin@affinix.com>
Date:   September 15th, 2003

This is a plugin to provide SSL/TLS capability to programs that
utilize the Qt Cryptographic Architecture (QCA).

Requirements:
  OpenSSL Library ([http://www.openssl.org/](http://www.openssl.org/))

Installation procedure:
  ./configure
  make
  su -c "make install"

This is what it's telling me to do.

I've done this to try and install it:
cd /tmp/fr-vUUep3/qca-tls-1.0

It changes the directory, but then I can't figure out how to make the configure part work.  I'm just real frusturated... between that, and the DVD player working intermittently... I'm baffled. Please help a huge n00b!  Thanks in Advance.

---

### Post by yabbadabbadont on 2007-06-08
It is already in the repositories.  You just need to install it using synaptic or apt-get or aptitude or adept...  :D

```
/home/daffy $ aptitude show qca-tls
Package: qca-tls
State: not installed
Version: 1.0-3
Priority: optional
Section: libs
Maintainer: Jan Niehusmann <jan@debian.org>
Uncompressed Size: 131k
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.2), libqt3-mt (>= 3:3.3.5), libssl0.9.8 (>= 0.9.8a-1), libstdc++6 (>= 4.0.2-4)
Description: TLS plugin for the Qt Cryptographic Architecture (QCA)
 This is a plugin to provide SSL/TLS capability to programs that utilize the Qt Cryptographic Architecture (QCA). 
 
 QCA is a library providing an easy API for several cryptographic algorithmns to Qt programs. 
 
 At the moment only the qca-tls plugin is packaged for debian, as it's used by the package 'psi'. The generic library and
 several other plugins will be packaged when upstream releases them.


```

---

### Post by Don_Juan on 2007-06-08
Thank you very much.  Using Synaptic, I figured out how to install it. Very easy....Thanks for pushing me in the right direction.  Any chance you know how to fix my DVD woes? lol

---

### Post by yabbadabbadont on 2007-06-08
Probably, but search the forums first as there are literally hundreds of threads on DVD problems.  Also read through this:  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by yabbadabbadont on 2007-06-08
If you do end up needing help with your DVD, please start a new thread on that topic.

---

