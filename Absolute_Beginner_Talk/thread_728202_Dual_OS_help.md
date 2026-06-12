---
title: "Dual OS help"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Djhump28 on 2008-03-18
I am running windows Xp media center edition, I want to try ubuntu, my Hard drive burned up and I had to replace it but I didn't have windows itself so I had to restore everything from the hp discs I had, and it partitioned the drive itself. I am curious is it possible to run both from the same partition or would I need a separate partition for ubuntu. Any help would be greatly appreciated.

---

### Post by zerhacke on 2008-03-18
Install Windows first, then install Ubuntu.  During the install phase of Ubuntu it will ask you how you want to partition.  The default option is to resize the Windows partition.

I suggest running chkdsk and defrag on the Windows drive before you resize the partition, as you can lose data at the end of the partition if you don't.

---

### Post by Duck2006 on 2008-03-18
You need a different partition to run ubuntu on as it runs on ext3 file system as win runs on a ntfs or fat32 file system.

---

### Post by zerhacke on 2008-03-18
Linux runs on much more than an ext3 filesystem...

---

### Post by bodhi.zazen on 2008-03-18
> **Djhump28 said:**
> I am running windows Xp media center edition, I want to try ubuntu, my Hard drive burned up and I had to replace it but I didn't have windows itself so I had to restore everything from the hp discs I had, and it partitioned the drive itself. I am curious is it possible to run both from the same partition or would I need a separate partition for ubuntu. Any help would be greatly appreciated.

Separate partition for Ubuntu if you want to install it to your hard drive. You can try Ubuntu, without installing, by booting the desktop CD or with VMWare, Virtualbox, or QEMU (virtualization will run from the .iso file).

You can even install Ubuntu into VMWare / VirtualBox / QEMU and 'install" ubuntu in the same partition as windows.

---

### Post by Djhump28 on 2008-03-18
thanks for the input so far I am gonna download it and check it out. I am shocked at how fast you guys responded to my post, much appreciated.

---

