---
title: "No kernel sources in Ubuntu 5.10"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by borzoi on 2006-08-22
Hello everybody,
I've to apply a test patch to 2.6 kernel, and installed Ubuntu 5.10, but it seems to me, it has no kernel sources.... am I wrong?

---

### Post by az on 2006-08-22
> **borzoi said:**
> Hello everybody,
I've to apply a test patch to 2.6 kernel, and installed Ubuntu 5.10, but it seems to me, it has no kernel sources.... am I wrong?

sudo apt-get install linux-source-2.6.12

You need to be online, since the kernel source is not on the cd.  It is in the main repository, online.

You do have the headers on the cd, which is enough to compile extra modules for your kernel


sudo apt-get install linux-headers-386

---

### Post by kwalo on 2006-08-22
> **azz said:**
> sudo apt-get install linux-source-2.6.12
sudo apt-get install linux-headers-386The package **linux-source**  always depends on the latest kernel version used in Ubuntu. It is worth to install a package **build-essential**, since programs needed to compile kernel are not installed by default. This package can be found on cd.

---

### Post by az on 2006-08-22
linux-source is only in Dapper and Edgy.  It was not in Warty (4.10) Hoary (5.05) or Breezy (5.10).  In those earlier releases, the kernel source is in a version-named linux-source package.

So for Breezy, it's "linux-source-2.6.12".

---

