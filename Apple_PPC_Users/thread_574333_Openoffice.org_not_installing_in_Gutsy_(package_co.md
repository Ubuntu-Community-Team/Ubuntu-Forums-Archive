---
title: "Openoffice.org not installing in Gutsy (package conflict)"
date: 2007-10-12
forum: Apple PPC Users
---

### Post by allesfresser on 2007-10-12
Hi, everyone.  I installed a Gutsy daily build on my iBook G4 a few days ago, and all seemed to go well (except for the top panel disappearing, but after turning off the desktop effects, which I was planning to do anyway, that's not a problem anymore).  I've since updated everything available (apt-get update and apt-get dist-upgrade), most recently just a few minutes ago.

But I've noticed that Openoffice.org is not available in the application menu.  I thought that was very strange since it's a standard component.  Upon checking what was going on with aptitude and apt-get, it appears that there are some package conflicts occurring that (IMHO) definitely should not be happening, especially with a distribution that's now in release candidate status.

The specific conflicts are as follows:

openoffice.org-common depends on openoffice.org-core (> 1:2.3.0)
    Available version of openoffice.org-core: 1:2.3.0~oog680m1-1ubuntu3

openoffice.org-core depends on openoffice.org-common (> 1:2.3.0-oog680m1)
    Available version of openoffice.org-common: 1:2.3.0-1ubuntu2

So there's a little bit of co-dependency going on here... :confused:

Anybody have any idea how to fix this (temporarily or permanently?)

UPDATE:  Bug filed for this issue in Launchpad:  [https://bugs.launchpad.net/ubuntu/+s...rg/+bug/152134](https://bugs.launchpad.net/ubuntu/+s...rg/+bug/152134)

---

### Post by allesfresser on 2007-10-12
Bug filed for this issue in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/152134]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/152134")

---

### Post by BladeMelbourne on 2007-10-12
I have the same issue with Gutsy PPC and haven't been able to get around it. Thanks for filing the bug.

---

### Post by chimaera on 2007-10-15
has been resolved, updates went in today just fine.

---

