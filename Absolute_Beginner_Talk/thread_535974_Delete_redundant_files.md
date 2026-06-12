---
title: "Delete redundant files"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by dr.koljan on 2007-08-27
Sometimes I install programs in a non-repo way, therefore I have to manually uninstall them later, which is not always clean. I am afraid there is a lot of redundant files on my hard drive, which I hate.

Is there a way to automatically scan for and delete files which do not belong to any packages?

Thanks :)

---

### Post by rexy on 2007-08-27
apt-cache pkgnames | xargs dpkg -L | sort -u  >  test

creates a list off all the files installed with packages. you could diff that against a complete file listing.  You could always try make uninstall for compiled sources. Or consider installing ompiled sources in a separate directory.

---

### Post by dr.koljan on 2007-08-27
> **rexy said:**
> you could diff that against a complete file listing.

Is there a program that could do that for me? Very weird if not, such tool is a must-exist :)

---

### Post by KIAaze on 2007-08-27
Or you could use [checkinstall]("http://www.asic-linux.com.mx/~izto/checkinstall/").

---

