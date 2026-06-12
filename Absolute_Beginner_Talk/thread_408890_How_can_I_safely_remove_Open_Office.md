---
title: "How can I safely remove Open Office???"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-04-13
Can I simply use Synaptic and do a Mark for Complete Removal? I want to just use Abi and Gnumeric...

---

### Post by rjfioravanti on 2007-04-13
using a terminal you should be able to do

sudo apt-get autoremove open-office.org

---

### Post by chunho on 2007-04-13
However, if you removed OpenOffice.org (OOo), you have to remove the Ubuntu metapackage. I think that the metapackage is used for updating the system.

Therefore I don't think it would be safe if you removed OOo.

---

### Post by zazen666 on 2007-04-13
> **chunho said:**
> However, if you removed OpenOffice.org (OOo), you have to remove the Ubuntu metapackage. I think that the metapackage is used for updating the system.

Therefore I don't think it would be safe if you removed OOo.



Can anyone confirm this?

---

### Post by aysiu on 2007-04-13
> **zazen666 said:**
> Can anyone confirm this?
From [the common questions page on the Wiki](https://help.ubuntu.com/community/CommonQuestions?highlight=%28commonquestions%29#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812): > **What is a meta-package? Is it safe to remove the ubuntu-desktop package?**
A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information.

It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade. 

---

