---
title: "Q.app"
date: 2007-12-29
forum: Apple Intel Users
---

### Post by stealthsniper96 on 2007-12-29
does anyone know how i can get Q to recognize my ubuntu partition? im using leopard on my mac side and ubuntu 7.10 on the linux side. and if not, are there any other free virtual machine programs?

---

### Post by alpinesatan on 2007-12-29
i dont think you can. os x doest recognised ext2/3 file systems to the best of my knowledge.
parallels is another choice of virtual pc.

kind regards

---

### Post by stealthsniper96 on 2007-12-30
ok thanks. do you know how i can get vmware to recognize my linux partition. it keeps telling me to make a new one.

---

### Post by tgalati4 on 2007-12-30
OS X Tiger has no problem reading and writing ext2/3.  I have formatted iPods and USB flashdrives and used external drives with Disk Utility.

---

### Post by alpinesatan on 2007-12-30
lol, well that makes sense :D esspecially build on unix lol.
So yea i guess all you need to do is mount the linux partition in os x.

---

### Post by stealthsniper96 on 2007-12-30
> **alpinesatan said:**
> lol, well that makes sense :D esspecially build on unix lol.
So yea i guess all you need to do is mount the linux partition in os x.

omg i know this is such a noob question. anyway. it was there when i first partitioned the drive with bootcamp but then after i installed linux it went away. how do i mount it again? 

fyi i installed it by deleting the BC partition andthen installing on the free space, which is probably why it got deleted. ;)

---

### Post by alpinesatan on 2007-12-30
lol, i tried to mount a linux partition before with no success sadly, even in disk utility it fails to mount lol, i fell upon this, 
[https://sourceforge.net/project/showfiles.php?group_id=64713&package_id=101149&release_id=468470](https://sourceforge.net/project/showfiles.php?group_id=64713&package_id=101149&release_id=468470)
i havent tried it.
Let me know how you get on.

Kind Regards

---

### Post by RC Howe on 2008-01-01
Ext2fs does work- I've used it. Unfortunately, you may have a hard time getting Q to recognize it because it may have issues with different drivers being installed, I have not tried it that way. However, more power to you if you can make it work.

---

### Post by cyberdork33 on 2008-01-02
I don't think you need to mount the partition before using it in Q, in fact, that may hinder it from working. You may, however, have to edit a config file manually to access a partition directly. If Q doesn't allow this, you might want to look for information on Qemu, which is what Q.app really is, just a prettified version of it.

---

