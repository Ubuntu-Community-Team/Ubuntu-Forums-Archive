---
title: "PPC gutsy ISO and dual processor utilization"
date: 2007-12-13
forum: Apple PPC Users
---

### Post by jazzybob on 2007-12-13
First, I tried using Ubuntu 7.04 on my venerable Powermac G4 dual processor (500mHz) - the distro only uses one processor, which made the entire process very slow.  Any suggestions?

Secondly, I tried to download the PPC gutsy ISO.  Burned as all my ISOs from canonical.  Both my Dual processor and my powermac (2005) refuse to load the CD.

Again, I tried the download on my AMD 64 as well as my G5 dual processor.

There are a hell of  a lot of G4s and G5s out here just waiting for  ubuntu (due to Apples planned obsolence of older models either due to bus speed or other architectual issues.  Keep ubuntu distros for the PPC community!

---

### Post by frog_pilot on 2007-12-13
For dual processor support you have to install 4 metapackages. Thats the whole deal. Simply execute```
sudo apt-get install linux-image-powerpc-smp linux-headers-powerpc-smp linux-restricted-modules-powerpc-smp linux-powerpc-smp
``` Reboot and voilà tout...

---

