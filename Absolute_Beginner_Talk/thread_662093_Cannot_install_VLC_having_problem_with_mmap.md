---
title: "Cannot install VLC having problem with mmap"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by stn2412 on 2008-01-08
I have been trying to install VLC and other media players but kept getting an error about not finding a file or folder in var/lib/dpkg/  called available. I added a folder called available and now i get the following :
dpkg: can't mmap package info file `/var/lib/dpkg/available': No such device
E: Sub-process /usr/bin/dpkg returned an error code (2)


Any thoughts?

---

### Post by stn2412 on 2008-01-08
Actually it's not just VLC either its dpkg in general, tried fixing it and I get the same error as if I was trying to install any package:
dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory

---

