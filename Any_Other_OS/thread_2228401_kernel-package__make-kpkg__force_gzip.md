---
title: "kernel-package / make-kpkg : force gzip"
date: 2014-06-07
forum: Any Other OS
---

### Post by makki76 on 2014-06-07
Hi,

I need to create a kernel (linux-image) for legacy systems (Debian lenny); this worked fine before but with recent ubuntu I have the problem that make-kpkg uses .xz-compression which the traget (dpkg 1.14) doesn't understand.
Is there some way to pass an option like "-Zgzip" to make-kpkg to force using gzip instead of xz ?

Michael

---

### Post by bapoumba on 2014-06-08
*Thread moved to **Other OS/Distro Support**.*

---

