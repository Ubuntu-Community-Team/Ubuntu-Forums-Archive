---
title: "wine +AMD64"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-07-20
Hi group,
I'd like to install wine.
I've zillions of files that I've created using MS Publisher 97.

Thing is, I think I've tried wine before and discovered an issue with AMD64 processors.
Phil

---

### Post by ravenwere on 2007-07-21
Try following this thread for starters:
[http://www.linuxforums.org/forum/ubuntu-help/63900-installing-wine-amd64.html](http://www.linuxforums.org/forum/ubuntu-help/63900-installing-wine-amd64.html)

regards,
r

---

### Post by Malibu Illusion on 2007-07-21
Rather than running a full-out chroot, you can install some 32-bit libraries and dependencies and force the architecture of a WINE deb file using the dpkg --force-architecture flag or, of course, compile from a source package.  I compiled the latest WINE version from the tarball sucessfully using this method yesterday on an AMD64 box.

You need something like the ia32-libs, ia32-libs-dev, ia32-libs-gtk and lib32asound2 packages.  You may need additional ones.

There are many resources on the web referencing this.

---

