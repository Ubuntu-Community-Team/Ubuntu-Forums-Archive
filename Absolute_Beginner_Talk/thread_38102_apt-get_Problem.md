---
title: "apt-get Problem"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by Dano on 2005-05-30
Why does this error keep coming up? what do i need in order to fix the problem?


W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems



Thanks a ton!
Dano

---

### Post by mostwanted on 2005-05-30
The file you're trying to download doesn't exist. Update your list and if that doesn't work, then try using another backports mirror.

---

