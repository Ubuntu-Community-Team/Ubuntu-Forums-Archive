---
title: "Nfs?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by jaybmx on 2006-08-17
What makes NFS so special? 

Can NFS on my Ubuntu box help make audio/video sharing on my network faster/better?

Thanks

---

### Post by gerbman on 2006-08-18
I've always found Samba to work perfectly for file sharing, and wouldn't switch to NFS for my purposes.

---

### Post by huygens on 2006-08-28
NFS is a filesystem to share drivers over a network just like if they are local. On all UNIX, you can share and mount (meaning use) NFS partition. For Windows, it is not installed by default, so if you intend to share data with Windows machine, this is perhaps not the easiest way...
Also, you should know that NFS under Linux used UDP instead of TCP (well that was the old time, now perhaps it can use TCP, but since I did not use NFS for a couple of years, I do not know if it is the default configuration). One drawback of UDP is the data integrity. If your network is busy and/or you have a HUB connecting all your computer, you might/will lose some packets of data. Thus, the video file you are downloading/reading from this NFS drive might be corrupted.
So Samba (SMB) is a better choice as it relies on TCP. It perhaps cannot compare in term of performance to NFS (and I am not even sure of that...), but it is reliable! Especially, to exchange data between two Linux boxes, Samba is pretty fast and hassle free :-) I do not know why SMB kept bugging me under Windows... Sometimes you do not see some files, over wireless connection, it crashes the connection, etc. But this is all Windows related... :-(

Huygens

---

### Post by handy on 2006-08-28
I found [this site]("http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT") to give me all I needed to set up NFS, in a P2P home network.

---

