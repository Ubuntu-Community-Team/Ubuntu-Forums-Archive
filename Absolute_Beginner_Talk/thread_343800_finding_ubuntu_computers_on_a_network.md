---
title: "finding ubuntu computers on a network"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by tekno62 on 2007-01-22
Ok I have 2 ubuntu computer one is dapper and one is edgy.  I would like to know how to share folders between the 2 computer as well as the windows pc.. I don’t see the ubuntu computers with Samba.

---

### Post by Shatrat on 2007-01-22
The easiest way I know is to right click on the directory you want to share on each ubuntu PC and use the Share Folder option.  It pops up a dialogue that helps you install and configure NFS and Samba.
samba is an implementation of the MS file and printer sharing service so it will be easy to work with the windows PC, although there is a bug in the edgy one that makes streaming audio and video across samba with ubuntu as client not work properly.
NFS is network file system and its simpler and more powerful, but windows won't be able to use it without some kind of NFS client, and I haven't tried any for windows so I dont know if there are any good ones.

---

