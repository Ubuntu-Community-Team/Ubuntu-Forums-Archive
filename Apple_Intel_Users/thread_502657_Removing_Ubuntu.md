---
title: "Removing Ubuntu"
date: 2007-07-16
forum: Apple Intel Users
---

### Post by soritong on 2007-07-16
I'm having issues removing Ubuntu from my Macbook. The Boot Camp utility won't work, and neither will Disk Utility. When I try to remove the partition via Disk Utility, it tells me that it contains a startup volume and cannot be removed.

Any help on getting rid of those partition without a complete reinstall of OS X? (I've lost my install CD, and Apple won't give me another one).

---

### Post by cyberdork33 on 2007-07-16
boot live cd, use partitioner to delete partition.

---

### Post by thully on 2007-07-16
After you do that, create a single partition to fill the empty space using the Installer and start installing to this partition (don't create a swap).  Cancel before the install is done, reboot into OS X, and now you will be able to use Boot Camp to restore your system to a single OS X partition.

If you want to use Ubuntu but are having trouble with a dual-boot, you can always try VMware Fusion or Parallels - they work pretty well for using Ubuntu with the exception of Compiz/Beryl...

---

