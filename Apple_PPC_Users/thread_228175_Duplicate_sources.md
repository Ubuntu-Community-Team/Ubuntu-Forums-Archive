---
title: "Duplicate sources"
date: 2006-08-02
forum: Apple PPC Users
---

### Post by Runarsv on 2006-08-02
W: Duplicate sources.list entry [http://is.archive.ubuntu.com](http://is.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/is.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-powerpc_Packages)
W: Duplicate sources.list entry [http://is.archive.ubuntu.com](http://is.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/is.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary
-powerpc_Packages)

How can I fix this problem.
RS

---

### Post by linear on 2006-08-02
Edit /etc/apt/sources.list to remove the duplicates.

In a Terminal:

**sudo nano /etc/apt/sources.list**

After editing:

[B]sudo apt-get update
[/B]

---

