---
title: "Libc6 on Drapper"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2007-02-17
This has been an ever growing problem, so far three programs I've wanted to install will not work because the version of libc6 isn't up to date enough. I need version 2.4, when I only have version 2.3.6, I've tried downloading it from Debian repositories and I ran into dependancy hell which I eventually couldn't fix. I think Edgy has the version I need but I'm on Drapper and I really don't want to have to upgrade just for one little package.

I am running Drapper Drake 6.04 64-bit edition.

Please help me, I REALLY need it.

-Ryan H

---

### Post by Maestro23 on 2007-02-17
.

---

### Post by po0f on 2007-02-17
Ryan H,

Upgrade to Edgy.  This is the only way you are going to get this to work.  And how is glibc "one little package"?  As far as importance/necessity, it is second only to the kernel!

---

### Post by az on 2007-02-17
> **Ryan H said:**
> This has been an ever growing problem, so far three programs I've wanted to install will not work because the version of libc6 isn't up to date enough. I need version 2.4, when I only have version 2.3.6, I've tried downloading it from Debian repositories and I ran into dependancy hell which I eventually couldn't fix. I think Edgy has the version I need but I'm on Drapper and I really don't want to have to upgrade just for one little package.

I am running Drapper Drake 6.04 64-bit edition.

Please help me, I REALLY need it.

-Ryan H

Don't ever try to install packages build for another distro or another release.  Just compile it from source.

The package manager is doing its job in preventing you from installing this package.  It is not binary-compatible with Dapper.  You need to backport it.  That means to compile it using the toolchain on your current system (dapper).   What package is it?


To upgrade to libc6, you need to dist-upgrade to Edgy or beyond...

---

### Post by SlayerMan on 2007-02-18
I have the same problem here (a package that needs a newer libc than the version installed on my dapper).

It seems that you cannot install multiple versions of libc on Ubuntu... which is very poor. Other distributions, e.g. Mandriva, have been able to have multiple libc versions installed for years (as separate RPM packages).

The only solutions seem to be to compile from source (needs a bunch of dev packages to be installed), build your own DEB, or upgrade to a newer version of Ubuntu.

---

### Post by gigaferz on 2007-02-23
how do i compile libc6 for kubuntu dapper 386?

I am afraid of "upgrading" for one package.

Correct me if I am wrong:
Download tar file, untar it , go into the new directory created , then I just type make??

I would appreciate some help.

I need it to use ndiswrapper utils 1.9 in kubuntu for a zonet usb wireless card.

Thank you

---

