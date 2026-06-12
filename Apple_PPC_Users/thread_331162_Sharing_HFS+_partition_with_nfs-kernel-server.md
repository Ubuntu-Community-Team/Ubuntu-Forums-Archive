---
title: "Sharing HFS+ partition with nfs-kernel-server"
date: 2007-01-04
forum: Apple PPC Users
---

### Post by calum on 2007-01-04
Is anyone successfully doing this, i.e. sharing out an HFS+ partition with nfs-kernel-server? I just get a "Permission denied" error at the client side when I try to mount it either on the local server itself (Edgy x86), or on a remote Mac (OSX, Powerbook G4). I can share out an ext3 filesystem just fine, and mount it on both.

The share works perfectly when I use nfs-user-server instead, but the user-server has a 2Gb file size restriction that makes it practically useless for me. Is there a known breakage wrt to the HFS+ filesystem and the kernel-server? If so, is there any way to get around the 2Gb limitation?

---

