---
title: "Duel boot 2 drives"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by KMW on 2008-02-05
This is a new continuation from thread "duel boot question" Started by Roque2.
Didn't want to hijack his thread anymore than I have. Would also like to thank dstew and everyone else who has helped so far.

So far we know that when booting to GRUB the option to boot to hdb is not listed and needs to be added to the GRUB menu.

dstew asked that I provide fdisk info so it fallows below. Hope dstew is still with me.

kevin@kevin-desktop:~$ sudo fdisk -l

Disk /dev/hda: 13.0 GB, 13022324736 bytes
255 heads, 63 sectors/track, 1583 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb743050e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1510    12129043+  83  Linux
/dev/hda2            1511        1583      586372+   5  Extended
/dev/hda5            1511        1583      586341   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec6d6f9f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1040     8353768+   7  HPFS/NTFS
/dev/hdb2            1041        4865    30724312+   5  Extended
/dev/hdb5            1041        4865    30724281    7  HPFS/NTFS
kevin@kevin-desktop:~$ 

Thanks again,Kevin

---

### Post by KMW on 2008-02-05
Bump for help!

---

### Post by gn2 on 2008-02-05
Maybe try a PM to whoever was helping on that thread?

Dual-booting with an OS on different drives can cause Grub to be confused.
Usually an edit cures it.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Or try this GUI tool: [http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391](http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391)
Ubuntu download lower down on the page.

---

