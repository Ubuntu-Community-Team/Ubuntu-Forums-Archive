---
title: "duplicate souces list message"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by obbe on 2007-06-16
hi all, i've a trouble with synaptic, when i open it, it shows this message:
```
W: Duplicate sources.list entry http://it.archive.ubuntu.com feisty/multiverse Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://it.archive.ubuntu.com feisty/multiverse Translation-it (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_i18n_Translation-it)
W: Duplicate sources.list entry http://it.archive.ubuntu.com feisty/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://it.archive.ubuntu.com feisty/universe Translation-it (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_feisty_universe_i18n_Translation-it)
W: Duplicate sources.list entry http://security.ubuntu.com feisty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://it.archive.ubuntu.com feisty-updates/multiverse Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_feisty-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://it.archive.ubuntu.com feisty-updates/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_feisty-updates_universe_binary-i386_Packages)
```

This is my sources.list:
```
deb http://it.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main universe restricted multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main universe restricted multiverse

deb http://it.archive.ubuntu.com/ubuntu/ feisty-updates main universe restricted multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ feisty-updates main universe restricted multiverse
```
any help?

---

### Post by skymera on 2007-06-16
i have duplicate awsell...
i ignore it.
i wanna know how to get rid of easy
rather than editing the /etc/apt/sources.list file.

---

