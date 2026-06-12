---
title: "Firefox 40.X.X PowerPC isn't available for all Ubuntu PPC flavours"
date: 2015-08-31
forum: Apple Hardware Users
---

### Post by xeno74 on 2015-08-31
Iceweasel and Firefox 40.X.X PowerPC aren't available for all Ubuntu flavours and for Debian with 32-bit userland currently.

There are build problems:

Iceweasel 40 build status: [https://packages.debian.org/de/experimental/iceweasel]("https://packages.debian.org/de/experimental/iceweasel")

Firefox 40 build status: [https://launchpad.net/ubuntu/+source/firefox/]("https://launchpad.net/ubuntu/+source/firefox/")

But iceweasel 40.0.3-1 was released for the unofficial Debian PPC64 port. I installed it inside my Debian PPC64 chroot. Unfortunately it doesn't start.

Error messages:

```

too much recursion
Segmentation fault

```

---

### Post by rican-linux on 2015-08-31
Same in Debian

---

### Post by xeno74 on 2015-09-07
Iceweasel was updated to version 40.0.3-3 for the unofficial Debian PPC64 port. I installed it inside my Debian PPC64 chroot. Unfortunately it doesn't start either.

---

