---
title: "nptl tls"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by tennisplaya05 on 2007-08-02
To start off, im running Feisty iin a 32 bit architecture.

well, i've been trying to run a playstation emulator in wine ( i already have the linux version of it; but i want to wine ePSXe for my own reasons). Only problem is that when i run it, i can't get it to find the essential video/audio plugins. My brother suggested that i use wine-kthread to run it, and this got it working for him. only problem is, whenever i try to run wine-kthread i get this:

wine: glibc >= 2.3 without NPTL or TLS is not a supported combination.
It will most likely crash. Please upgrade to a glibc with NPTL support.
Segmentation fault (core dumped)

i have glibc updated to its latest version. (i have both glibc_2.5.0-0exp1 and glibc_2.5.0-0exp2 installed) so where is the problem?

Do i need to update wine to the bleeding edge version? (im running version 0.9.42)

And could someone explain to me what kthread does?

thanks.

---

