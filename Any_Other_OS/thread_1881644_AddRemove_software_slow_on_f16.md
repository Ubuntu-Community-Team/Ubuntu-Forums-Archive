---
title: "Add/Remove software slow on f16"
date: 2011-11-15
forum: Any Other OS
---

### Post by layers on 2011-11-15
So, I installed Fedora 16 to give it a whirl, and everything is great so far, except the Add/Remove program. Every time I search something in it, it takes 2 min to display a list of options. I though it's ok for the first time, but not now. Is it the same with everybody else?

---

### Post by boydrice on 2011-11-16
I don't use Packagekit to add or remove software, but YUM works fine for me.  What you are describing sounds like YUM rebuilding its cache.  I am pretty sure this can be modified in yum.conf, not sure if that will fix if for Packagekit or not.

---

### Post by crdlb on 2011-11-17
You might find the alternative package manager [Zif]("http://people.freedesktop.org/~hughsient/zif/") interesting. Basically, PackageKit's author argues that a package manager designed to be used from the command line (and written in python) is not a good fit for PackageKit. AFAICT, the main barrier to the Zif backend being used by default is that it and yum do not use the same dependency-resolving code (yet).

---

