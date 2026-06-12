---
title: "apt-get update problem..."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-10-18
I just moved and I finally got my internet connection. I tried to run apt-get update and I got this error.
```
grim@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://packages.freecontrib.org dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.canonical.com dapper-commercial Release
Get:6 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://packages.freecontrib.org dapper Release
Err http://packages.freecontrib.org dapper Release

Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Get:7 http://packages.freecontrib.org dapper Release [9452B]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://packages.freecontrib.org dapper Release
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://packages.freecontrib.org dapper/non-free Sources
Fetched 9646B in 1s (5324B/s)
Reading package lists... Done
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
grim@ubuntu:~$

```

What is a public key? Does it have something to do with me moving to a new house?

---

### Post by PriceChild on 2006-10-18
Nope.

It is  an encrypted piece of information, which allows you to check "signatures" on packages you download to ensure that they haven't been tampered with before they get to you from the person who built them.

You can add keys in synaptic if you can find the package maintainer's key.

---

