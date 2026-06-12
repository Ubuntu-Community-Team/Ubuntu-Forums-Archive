---
title: "Install a Breezy program in Dapper?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-07-30
There's a program kcdlabel [http://kcdlabel.sourceforge.net/](http://kcdlabel.sourceforge.net/) that exists as a package in Breezy, but not in Dapper--which I'm running.

It's here: [http://packages.ubuntulinux.org/breezy/source/kcdlabel](http://packages.ubuntulinux.org/breezy/source/kcdlabel)

Is there an easy way to install this in Dapper? Because I have no idea what I should be downloading (one of the files is 0 bytes) or what to do with it/them after downloading.

---

### Post by Kilz on 2006-07-30
> **editrix said:**
> There's a program kcdlabel [http://kcdlabel.sourceforge.net/](http://kcdlabel.sourceforge.net/) that exists as a package in Breezy, but not in Dapper--which I'm running.

It's here: [http://packages.ubuntulinux.org/breezy/source/kcdlabel](http://packages.ubuntulinux.org/breezy/source/kcdlabel)

Is there an easy way to install this in Dapper? Because I have no idea what I should be downloading (one of the files is 0 bytes) or what to do with it/them after downloading.

I took a tlook, this file kcdlabel_2.13-KDE3.orig.tar.gz 	646.9 	a384147c5bdbe08f64356fe31eb12249 is a source package. The other 2 are patches. The program needs to be compiled.
Extract the archive
Open a terminal
```
Cd /path/to/extracted/
 ./configure
make
sudo make inslall
```

---

### Post by editrix on 2006-07-30
Thanks, Kliz, but now I have another question:

I've read it's a bad idea to use programs from a newer release of (K)Ubuntu with an older, because it could break something. What about the other way around?

---

### Post by Lord Illidan on 2006-07-30
> **editrix said:**
> Thanks, Kliz, but now I have another question:

I've read it's a bad idea to use programs from a newer release of (K)Ubuntu with an older, because it could break something. What about the other way around?

It might not break anything, but you could run into dependency errors. Generally, it is not recommended. If there is no .deb package, compile it..

---

