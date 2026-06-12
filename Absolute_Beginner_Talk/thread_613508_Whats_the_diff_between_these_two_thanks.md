---
title: "Whats the diff between these two thanks"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by ronaldor9 on 2007-11-15
whats the diff between Network File System (NFS) and having a shared folder through samba ??

thanks

---

### Post by delphiguy on 2007-11-15
from what I understand NFS is the protocol to use to share files between linux machines.
And since there is not NFS client for windows, if you want to share your files from Linux to Windows you have to use samba.

Hope this makes sense.

---

### Post by disturbed1 on 2007-11-15
NFS is available for Windows ([google]("http://www.google.com/search?hl=en&q=NFS+windows&btnG=Search") is your friend [SIZE=-1]**2,590,000 hits**[/SIZE] ;) ). Samba is a protocol used to **Browse** folders/drives/printers that have Windows File & Printing sharing enabled on them.

NFS stands for Network File System. NFS will allow you logically mount a folder/drive/directory as an entire file system. 

[quote="http://en.wikipedia.org/wiki/Network_File_System_(protocol)"]allowing a user on a client [computer]("http://en.wikipedia.org/wiki/Computer") to access files over a [network]("http://en.wikipedia.org/wiki/Computer_network") as easily as if the network devices were attached to its local disks.[/quote]

If your just looking to have easy access to your Linux files on a Windows machine, SAMBA is an easy way to do this. If you're looking for a more perminent/reliable method go for NFS. Both require a setup procedure including users, passwords, inport/export options. The Ubuntu Wiki has entries and walk throughs on how to set both up.

---

