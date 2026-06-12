---
title: "How to uninstall LinuxMint?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by ebeckhusen on 2007-11-02
Okay, so I thought I'd try out LinuxMint.  I installed it on a separate partition and now I'd like to get rid of it.  Do I just delete the partitions?  If so, how?  And how do I get Grub to recognize that I only have the Ubuntu Os on the machine after I get rid of LinuxMint?

---

### Post by BrendanM on 2007-11-02
Deleting the partition would work fine. You can use Gparted partition editor to delete it. After you've done that, you can edit /boot/grub/menu.lst to remove LinuxMint from the boot menu.

---

