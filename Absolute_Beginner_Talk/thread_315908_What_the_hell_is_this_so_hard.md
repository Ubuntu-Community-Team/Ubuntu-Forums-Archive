---
title: "What the hell is this so hard?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-12-09
i have to transfer a bunch (29GB) of files from my desktop to my laptop.  I am borrowing my friends router and have both machines connected to it as verified by both of them saying that they are connected and the router saying two devices are attached.  BUT i can not see either in (Places >) Network Servers.

Both machines are running ubuntu (one dapper and edgy).  What I am i suppose to do??????](*,)

---

### Post by moshuptrail on 2006-12-09
are you trying to use samba or ftp?

samba will let you do the equivalent of windows networking
you'll need to make sure both are in the same workgroup, etc

with ftp, you need to set up one as an ftp server
the other as a client

---

### Post by insub2 on 2006-12-09
whatever works?
what should i do?

---

### Post by K.Mandla on 2006-12-09
> **insub2 said:**
> whatever works?
what should i do?
Setting up [NFS]("http://www.ubuntuforums.org/showthread.php?t=249889") is very fast and very easy. Make one machine the server and one the client and it's just like moving a file in Nautilus.

---

### Post by moshuptrail on 2006-12-10
NFS - I had just about forgotten that option.  Haven't used it in years.
Read up on NFS and FTP and see what you think is easer.

---

### Post by insub2 on 2006-12-10
> **K.Mandla said:**
> Setting up [NFS]("http://www.ubuntuforums.org/showthread.php?t=249889") is very fast and very easy. Make one machine the server and one the client and it's just like moving a file in Nautilus.

That worked and was easy enough when following those instructions.  Thank you.

---

