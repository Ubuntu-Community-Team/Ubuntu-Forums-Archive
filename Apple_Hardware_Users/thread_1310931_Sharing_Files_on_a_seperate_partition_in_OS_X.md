---
title: "Sharing Files on a seperate partition in OS X"
date: 2009-11-02
forum: Apple Hardware Users
---

### Post by brucem91 on 2009-11-02
Hello. I have a question. I just did a fresh install of ubuntu 9.10 and snow leopard on my mac. I gave OS X 250 GB, I made a 120ish GB fat32 partition for my files, and then the rest I installed ubuntu on. Now ubuntu can mount the fat32 partition no problem. However, OS X does not seem to want to mount the fat32 partition. Any suggestions. I would love to put all my files on the fat32 partition, that way I do not have to transfer anything when switching OS's.

---

### Post by tuwe on 2009-11-02
hi.

I believe os x does not know about fat32 out of the box, although i have no experience with that.

I installed OS X and Ubuntu in such a way that they share a home directory. This however involves synchronizing uid and gid between OSX and Ubuntu, and probably there is a significantly less painful way to achieve what you want to do.

---

### Post by maflynn on 2009-11-02
> **tuwe said:**
> hi.

I believe os x does not know about fat32 out of the box, although i have no experience with that.

Incorrect, OSX can read/write to FAT32

I use a partition for just this purpose, its FAT32 and allows me to share files between OSX and Fedora.

There's also thumb drives that will do the same thing if you don't want to create a new partition, which btw, is formatted to FAT32 as well.

---

