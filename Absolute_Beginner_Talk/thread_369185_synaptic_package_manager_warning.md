---
title: "synaptic package manager warning"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by spacegypsy on 2007-02-24
Hi;

Can somebody explain why I get a warning after reloading package information in Synaptic Package manager?

This is what is says:

> The following problems were found on your system:

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)

How do I solve these porblems?

thx

---

### Post by grogger13 on 2007-02-24
check out your source.list file and look for those directories printed multiple times,  just delete all but one of them, (just search source.list if you dont know where it is)

---

### Post by spacegypsy on 2007-02-24
Thx grogger13,

Is het possible that it is sources.list and not source.list like you wrote?

---

### Post by Maestro23 on 2007-02-24
> **spacegypsy said:**
> Thx grogger13,

Is het possible that it is sources.list and not source.list like you wrote?

Path to sources.list

> /etc/apt/sources.list


---

### Post by spacegypsy on 2007-02-24
I only found this one in double;

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

and deleted one of them

---

### Post by spacegypsy on 2007-02-24
problem solved :)

---

