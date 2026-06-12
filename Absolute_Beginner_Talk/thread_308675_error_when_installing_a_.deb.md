---
title: "error when installing a .deb"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by tee2 on 2006-11-28
I'm trying to install nero for linux via a .deb and I get an error saying "Error: Dependency is not satisfiable: xlibs"

Does that mean its not in the repositories I have?

---

### Post by Zarephath on 2006-11-28
It means that you need to install xlibs first for a dependency to be met. Once you do this you may see other items it says need to be installed as well. There should be a README file or something like it that explains what the dependencies are..that way you can use apt-get to install them. For example sudo apt-get install xlibs should install the xlibs

---

### Post by ajgreeny on 2006-11-28
I don't think xlibs is available any more in the repos so get a copy of xlibs-dummy.zip which unpacks to xlibs-dummy.deb which you can install and takes the place of xlibs by fooling the system into thinking xlibs is installed.  I've done it in dapper and it works OK, but I can't remember where I got it from so have added it as an attachment.

---

### Post by tee2 on 2006-11-28
thanks ajgreeny!

---

### Post by to4i on 2007-02-15
> **ajgreeny said:**
> I don't think xlibs is available any more in the repos so get a copy of xlibs-dummy.zip which unpacks to xlibs-dummy.deb which you can install and takes the place of xlibs by fooling the system into thinking xlibs is installed.  I've done it in dapper and it works OK, but I can't remember where I got it from so have added it as an attachment.
Thank you! Nice one :)

---

### Post by busta87 on 2008-02-05
> **ajgreeny said:**
> I don't think xlibs is available any more in the repos so get a copy of xlibs-dummy.zip which unpacks to xlibs-dummy.deb which you can install and takes the place of xlibs by fooling the system into thinking xlibs is installed.  I've done it in dapper and it works OK, but I can't remember where I got it from so have added it as an attachment.

Thanks alot for that Dl it helped me out

---

