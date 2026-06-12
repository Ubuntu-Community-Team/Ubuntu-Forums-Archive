---
title: "Pybliographer won't uninstall"
date: 2007-09-27
forum: Apple PPC Users
---

### Post by chichibabin on 2007-09-27
Hi Just installed Ubuntu on a Powerbook G4. Tried to install pybliographer via synaptic but it threw an error at the end. It is now impossible to remove the package. 

```

sudo apt-get remove pybliographer
After unpacking 2351kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115197 files and directories currently installed.)
Removing pybliographer ...
Segmentation fault (core dumped)
dpkg: error processing pybliographer (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 pybliographer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems like a bug in the package. Problem is I can't remove the package now. Can someone help me remove it?
Cheers,
Sat

---

### Post by ajgreeny on 2007-09-27
What about trying synaptic and its **"Fix broken packages"** in the Edit menu.  I don't know if it will work, but it must be worth a try.

Failing that try purging the package with the **--purge** option.  Again, I don't see why that would work if **remove** alone won't, but worth a try.

---

