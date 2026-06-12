---
title: "update error"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by tekno62 on 2007-02-10
ok 
I getting the little error - just need to have an idea where to find it so i can kill it


W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)

---

### Post by DerArzt on 2007-02-10
enter
[HTML]sudo gedit /etc/apt/sources.list[/HTML]
into a terminal.

In here you should find each of the two entries twice. delete one of each of them.

---

