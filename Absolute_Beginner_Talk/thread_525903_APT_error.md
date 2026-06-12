---
title: "APT error"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by kklingerman on 2007-08-14
Hi,

  I had a package hang during install.  Now when I run a APT-INSTALL, I get the following:

E: The package hl1440lpr needs to be reinstalled, but I can't find an archive for it.

  The same type of error comes up when I run Synaptic Package Manager.  How do i get rid of this package and get APT running again?  Thanks.

---

### Post by bwtranch on 2007-08-14
Run gedit /var/lib/dpkg/status and delete the offending entry and save. Then go to Synaptic and delete the partially installed package.

---

