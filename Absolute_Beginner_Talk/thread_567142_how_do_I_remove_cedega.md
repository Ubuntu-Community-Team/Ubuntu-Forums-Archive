---
title: "how do I remove cedega?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-04
idem

EDIT: ```
sudo apt-get remove cedega-small
```

---

### Post by Yoooder on 2007-10-04
I presume by your edit you've figured it out.

Let me give you a tip/pointer...  use 'aptitude' instead of 'apt-get' for package management.  Aptitude uses the same mechanisms and command-line arguments as apt-get but it also tracks the reasons why it installs programs.

An example:

If I do 'apt-get install kubuntu-desktop' and then 'apt-get remove kubuntu-desktop' I will actually only be removing the virtual package for kubuntu-desktop.  When it is installed the virtual-package will depend on a lot of other real packages that comprise kubuntu--so to actually remove everything that was installed would require an 'apt-get remove...' with about 70 package names.

If I do the same thing using aptitude it will track that when I requested kubuntu-desktop that the package in turn required those 70 other packages as dependencies--and that I wasn't explicitly asking for them.  Then if I do an 'aptitude remove kubuntu-desktop' it will remove all of the no-longer-needed dependencies.

aptitude really is a wonderful tool, and you can substitute it for nearly every apt-get task including installs, removes, updates, upgrades, and dist-upgrades.

---

### Post by internetishere on 2008-02-20
thanks that helped me out.

---

