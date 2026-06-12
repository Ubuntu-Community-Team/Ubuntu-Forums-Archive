---
title: "Dual booting"
date: 2011-11-13
forum: Any Other OS
---

### Post by UncleMonty on 2011-11-13
Is there a simple way of dual booting linux mint and ubuntu?

---

### Post by oldfred on 2011-11-13
I do not know Mint but I thought it now used grub2 also, So either should boot both systems.

I do know that the os-prober in Ubuntu finds other systems and adds them to the boot menu and works in almost all cases.
```
sudo update-grub
```

You just have to decide which you will boot the most and have it in the MBR so it is first on the menu. The one you install last will normally be the one installed to the MBR by default, but you can easily reinstall another grub2 based system into the MBR.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

