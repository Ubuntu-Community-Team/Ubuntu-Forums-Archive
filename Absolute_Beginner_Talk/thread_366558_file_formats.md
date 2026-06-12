---
title: "file formats"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by amod on 2007-02-21
i heard that ubuntu requires .deb files for installing any software.. i hav downloade a coulpe of utilities (eg. for my net for which i am very grateful to this forum)but they r in da rpm file format.Wat i would like to know is dat will this format be recognized by ubuntu or will i hav to convert them to .deb format. and if so then how???

---

### Post by erkki70 on 2007-02-21
Hi,
You can use alien to convert .rpm
Have look to this tutorial.
[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)
Good luck :-)

---

### Post by louis_nichols on 2007-02-21
You need to convert them from rpm to deb.

This is easily done with a package called [alien]("http://packages.ubuntu.com/edgy/admin/alien"). Just install it from synaptic. Then, when you download a package as rpm just use
```
alien *path-to-package *
```

Then you can install the deb as usual. But be careful that not all packages will eork. There are some differences that could make a package incompatible. Mys uggestion is to make an effort to search the native deb equivalent of a package. Ubuntu has one of the biggest software repositories out there and an active community that continously packages new software.

---

