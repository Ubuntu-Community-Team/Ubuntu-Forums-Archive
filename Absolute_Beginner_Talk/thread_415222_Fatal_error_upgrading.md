---
title: "Fatal error upgrading"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Hurricane on 2007-04-20
Hi, trying to upgrade edgy to feisty.  Receive the following error which it tells me to report:


Traceback (most recent call last):

  File "/tmp/tmpmpmnoT/feisty", line 56, in ?
    app.run()

  File "/tmp/tmpmpmnoT/DistUpgradeControler.py", line 1025, in run
    self.fullUpgrade()

  File "/tmp/tmpmpmnoT/DistUpgradeControler.py", line 962, in fullUpgrade
    if not self.updateSourcesList():

  File "/tmp/tmpmpmnoT/DistUpgradeControler.py", line 390, in updateSourcesList
    if not self.rewriteSourcesList(mirror_check=True):

  File "/tmp/tmpmpmnoT/DistUpgradeControler.py", line 302, in rewriteSourcesList
    if ((len(self.cache[pkgname].candidateOrigin) == 0)

  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 82, in __getitem__
    return self._dict[key]

KeyError: 'ubuntu-minimal'



Any ideas?  Much appreciated

---

### Post by Hurricane on 2007-04-20
Just to add, when attempting the command line upgrade, I get the following:

matthew@matthew-desktop:~$   sudo apt-get install ubuntu-minimal ubuntu-standard 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-minimal is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-minimal has no installation candidate
matthew@matthew-desktop:~$

---

### Post by Hurricane on 2007-04-20
Fixed- enabled all sources in Administration/Software sources.

---

### Post by HiJolly on 2007-04-20
How does one enable all sources?

HiJolly

---

### Post by Hurricane on 2007-04-20
I went to Administration>>Software Sources and checked everything, and now it all works.

---

