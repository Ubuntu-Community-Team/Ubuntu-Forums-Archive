---
title: "KDE install problem"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by utab on 2006-02-24
hi all,

sudo apt-get install kde

giving this error

Reading package lists... Done
Building dependency tree... Done
Package kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bi nary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package kde has no installation candidate

problem?

thx.

---

### Post by Perfect Storm on 2006-02-24
Try update your sourcelist first:

```
sudo apt-get update
```

Edit: If you want to install KDE

You might want to do this instead:

```
sudo apt-get install kubuntu-desktop
```

---

