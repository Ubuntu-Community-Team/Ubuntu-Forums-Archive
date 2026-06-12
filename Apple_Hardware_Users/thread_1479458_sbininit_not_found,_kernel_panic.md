---
title: "/sbin/init not found, kernel panic"
date: 2010-05-10
forum: Apple Hardware Users
---

### Post by bjesus on 2010-05-10
Hey,
I'm trying to install Ubuntu Server 10.04 on a PPC G4 PowerMac.

It took a while, but finally I managed to get through the installation.

Unfortunately, after choosing Ubuntu from the yaboot menu at startup, it takes a moment and then displays a kernel panic about not founding /sbin/init .

Well, /sbin/init is there for sure (I've checked again, using the CD).

What could be the problem?
Any hints?

Thanks!:popcorn:

---

### Post by bjesus on 2010-05-11
Anyone? Any idea? Am I doing something very rare trying to install Ubuntu 10.04 to a PPC machine?

---

### Post by linuxopjemac on 2010-05-12
your yaboot loader is not setup correctly. Chroot into your system from a live cd and find out where linux is installed, on which partition. You then need to manually adapt yaboot.conf and run ybin -v. Read the following posts and you will find the solution.

[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

