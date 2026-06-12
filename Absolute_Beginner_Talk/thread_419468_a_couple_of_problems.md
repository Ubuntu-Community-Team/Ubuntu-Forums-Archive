---
title: "a couple of problems"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-04-23
When i run:
```
$ apt-get update
```
it gives me this:
```
Err http://ftp.iinet.net.au Edgy/main Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy/restricted Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy/universe Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy/multiverse Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy/main Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy/restricted Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy/universe Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy/multiverse Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-updates/main Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-updates/restricted Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-updates/universe Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-updates/multiverse Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-updates/main Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-updates/restricted Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-updates/universe Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-updates/multiverse Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-security/main Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-security/restricted Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-security/universe Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-security/multiverse Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-security/main Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-security/restricted Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-security/universe Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-security/multiverse Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-backports/main Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-backports/restricted Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-backports/universe Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-backports/multiverse Packages
  404 Not Found
Err http://ftp.iinet.net.au Edgy-backports/main Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-backports/restricted Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-backports/universe Sources
  404 Not Found
Err http://ftp.iinet.net.au Edgy-backports/multiverse Sources
  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy/main/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-updates/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-updates/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-updates/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-updates/main/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-updates/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-updates/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-updates/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-security/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-backports/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-backports/main/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-backports/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-backports/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/Edgy-backports/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

and when i try to compile a gtk engine i get:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

any help is appreciated,
Ta,
Nolander.

---

### Post by crispy_420 on 2007-04-23
As for the first part, looks like servers are down. You got here so it is not your connection. Maybe try back later.

---

### Post by Nolander on 2007-04-23
problem 1: Solved

Problem 2: pending

---

### Post by nsleiman on 2007-04-23
are you sure its ** E**dgy-updates or **e**dgy ?

---

### Post by dreadlord_chris on 2007-04-23
> **Nolander said:**
> problem 1: Solved

Problem 2: pending

Problem 2: install the _build-essential_ package
```

sudo apt-get install build-essential

```

---

