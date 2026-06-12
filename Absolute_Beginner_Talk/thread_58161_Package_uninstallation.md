---
title: "Package uninstallation"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by Aussiein on 2005-08-19
Hi All,

I am new to Ubuntu.

 My question is "what happens to dependnecies of the package when it is uninstalled via apt-get " ?

Are they reomved as well ? Is there  a way to keep the dependencies without package ?

Thanks in advance.

Aussiein

---

### Post by heimo on 2005-08-19
Short answer: Dependencies are not removed with apt-get remove, only the packages that depend on the packages you remove.

These threads will answer your questions:
[http://www.ubuntuforums.org/showthread.php?t=53150](http://www.ubuntuforums.org/showthread.php?t=53150)
[http://www.ubuntuforums.org/showthread.php?t=53176](http://www.ubuntuforums.org/showthread.php?t=53176)

---

### Post by FLeiXiuS on 2005-08-19
Yes you can go through and delete the package with the backend of apt.  

dpkg would be what your looking for.

**Manual**
$ man dpkg

**Removing Packages**
$ dpkg -r PACKAGENAME

**Installing Packages**
$ dpkg -i PACKAGENAME

**Force Removing**
$ dpkg -r --force-depends

---

### Post by Aussiein on 2005-08-19
Many thanks for the help

---

