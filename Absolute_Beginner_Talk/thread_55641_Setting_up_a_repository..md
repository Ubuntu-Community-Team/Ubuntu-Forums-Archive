---
title: "Setting up a repository."
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by cnayak on 2005-08-09
I think my college server has a complete mirror of archive.ubuntu.com  I'm not sure if it may help or not, but here's the id ( it's an internal network)

 [ftp://ftp.iitb.ac.in/os/ubuntu/i386/archive.ubuntu.com/pool/](ftp://ftp.iitb.ac.in/os/ubuntu/i386/archive.ubuntu.com/pool/)

 nw this has folders like main,multiverse,universe and restricted. Each has a neat alphabetical index of softwares. Can I use this as an repository?

---

### Post by tonym on 2005-08-11
Assuming it is a mirror you should be able to.  Update your /etc/apt/sources file.

Specify the source you give above,  minus the "/pool".  ie you need to specify the directory that includes in it a "dists" directory.

---

