---
title: "Circular Dependencies"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Qon on 2007-01-01
Before I begin, please forgive me if this isn't a correct section - I couldn't find one that would suit this question better, as the installation subforum seemed to be about the OS installation, rather than packages. Anyway, on to the problem at hand...

I've downloaded a package that depends on the libpango library and doesn't seem to accept the version installed automatically with Dapper. So I figured I'd download the latest version and install it - mind you I don't have internet access on my linux box, so I DLed everything as files - all looked nice until I run the packages and it turns out libpango depends on libpango-common and libpango-common depends on libpango. The package manager doesn't seem to allow me to install either because of the circular dependency, and I'm stumped. Any ideas about a solution? Could I perhaps force the installation of both somehow?

Thanks in advance.

---

### Post by Crooksey on 2007-01-01
Download all files, here: [http://packages.debian.org/stable/libs/libpango1.0-0](http://packages.debian.org/stable/libs/libpango1.0-0)

Place them in one directory then try the install.

---

### Post by Qon on 2007-01-01
That version is older than the one that comes by default with Dapper, and neither is good enough for the package I'm trying to install. It seems to want the latest, 1.14, version.

---

