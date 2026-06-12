---
title: "Ubuntu 7.10, Terminal, command line error"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by rlhanson on 2007-11-08
When I attempt to install a .tar.bz2 package everything is fine until I try to do the ./configure line command then I get a command not found error. Anyone else had this problem?

---

### Post by Maestro23 on 2007-11-08
> **rlhanson said:**
> When I attempt to install a .tar.bz2 package everything is fine until I try to do the ./configure line command then I get a command not found error. Anyone else had this problem?

When installing from soruce (tar file), you need "build-essential" installed first.

> sudo apt-get install build-essential

Installing from Source: [http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

*Also when you extract a tarball, there should be a README/INSTALL doc in the folder with instructions.

---

