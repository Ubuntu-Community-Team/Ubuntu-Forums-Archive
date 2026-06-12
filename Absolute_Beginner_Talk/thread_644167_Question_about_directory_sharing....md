---
title: "Question about directory sharing..."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Lord Xadar on 2007-12-18
Well well well... this is what I want to do but haven't had success doing:

I want to "share" a single folder (my _~/Public_ folder)... what do I mean?
Well, PC1 has the folder, and I only need other PCs in my network to get full read/write access to it.

What have I done so far:
System > Administration > Shared folders
Installed SMB and NFS
Added the folder
unticked "Read Only"

The other PCs can read the the files in the share but can't write or delete them, nor create files in the share.

made a chmod 777 of the share... well... now the other PCs can create files... but new files created in the share by my user on PC1 still have write rights only for proprietary and not "group and others".

I remember this was easier in earlier versions of ubuntu...
(what does ticking/unticking "Read Only" does so far?)
It seems that local rights have more priority than "samba rights"...

---

### Post by hyper_ch on 2007-12-18
are the other machines linux or windows machines?

---

### Post by Lord Xadar on 2007-12-18
Linux machines.
Distro: Ubuntu 7.10

No firewall installed, every machine is connected to a Router, they get a static IP from the Router's DHCP server.

---

### Post by bodhi.zazen on 2007-12-18
Well, first decide on a protocol, nfs or samba.

I like nfs personally :)

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Once you decide on a protocol, tell us which one and what you have done to configure the server.

---

### Post by Lord Xadar on 2007-12-18
I'm going with Samba, there are also Windows machines in my net... but the question now is to make the linux machines work as I said before.

---

### Post by Lord Xadar on 2007-12-19
[SIZE="1"]Bump...[/SIZE]

---

