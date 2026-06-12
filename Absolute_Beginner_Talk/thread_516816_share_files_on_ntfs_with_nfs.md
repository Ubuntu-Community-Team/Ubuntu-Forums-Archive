---
title: "share files on ntfs with nfs"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by captlogic on 2007-08-03
I want to share files between two linux pc's using nfs.

The first share (on ext3) works just fine
The second share (on ntfs) does not work. Client computer reports host says permission denied.

I now get it, you can't set permission on an ntfs drive, and thus cannot share via nfs.  Is that a correct assumption?

Is there a workaround?

Thanks for your help

---

### Post by bodhi.zazen on 2007-08-03
I assume the nfs is on a Windows box ?

NFS is available to windows : 

[http://doc.gwos.org/index.php/MountNFS](http://doc.gwos.org/index.php/MountNFS)

[http://www.openfree.org/pet/index.php/Mount_an_NFS_share_from_Windows](http://www.openfree.org/pet/index.php/Mount_an_NFS_share_from_Windows)

If you are on linux see this :

[http://www.ntfs-3g.org/support.html#nfs](http://www.ntfs-3g.org/support.html#nfs)

---

### Post by captlogic on 2007-08-03
sorry I didn't clarify.

The ntfs drive is a USB drive with data only. I'm running Feisty.  So FUSE is the direction I need to go?

Thanks again

---

### Post by bodhi.zazen on 2007-08-03
Yes, but I can not give you step-by-step directions for Ubuntu.

Here is a thread from Fedora : [http://forums.fedoraforum.org/showthread.php?t=159877](http://forums.fedoraforum.org/showthread.php?t=159877)

---

