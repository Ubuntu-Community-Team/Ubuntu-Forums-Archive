---
title: "install package from .bz2"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by pirozzi on 2005-11-16
i'm brand new to debian, so sorry for the silly question. i need to install skype package from the tar .bz2 and i don't know how to manage it. should i follow the standard installation procedure (extract, configure, make, make install)? how does it work with ubuntu?

---

### Post by vruum on 2005-11-16
skype already has a .deb package, that should work on ubuntu. download that to your homedirectory, open up a terminal and type
```

sudo dpkg -i skype_1.2.0.18-1_i386.deb

```
to install. Configure make etc.. is for source packages, and i don't think skype releases source.

---

### Post by pirozzi on 2005-11-16
i've already tryed with the .deb package, but unfortunately it doesn't work. dpkg -i give me back a dipendence error. on the other hand i've read the the .bz2 (i suppose to be a source) seems to work fine.

---

### Post by psyguy92 on 2005-11-16
[QUOTE=pirozzi]i've already tryed with the .deb package, but unfortunately it doesn't work. dpkg -i give me back a dipendence error. on the other hand i've read the the .bz2 (i suppose to be a source) seems to work fine.[/QUOTE]

If you tried this one:
Debian package (7.7 MB)
Xandros, MEPIS, Ubuntu, other Debian-based distros

Please try this one from their download page instead:
Static binary tar.bz2 with Qt 3.2 compiled in (10.4 MB)

I had a  lib version conflict when trying the standard .deb on their site (the one without Qt).  I think a KDE package I happen to have depends on the installed version (but I could be mis-remembering).  Anyhow, I found I could not get rid of the version of the conflicting package in order to install the correct dependency.  I believe this is what is happening with you.

The one with Qt compiled in should work.  I believe you need to download the file and decompress it, and then execute the program using *./program-name*.  I'm on a slow connection at the moment, or I'd download and double-check.

Good luck!

---

