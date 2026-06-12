---
title: "Win8 and existing Win7 dual boots"
date: 2012-11-03
forum: Any Other OS
---

### Post by Eggnog on 2012-11-03
I've got Win7 and Ubuntu dual booting with EasyBCD controlling the boot through Win7.  If I "upgrade" to Win8 somewhere down the road, will it overwrite the MBR or otherwise trash my existing EasyBCD menu or will it leave it alone?  Anyone know?

---

### Post by critin on 2012-11-04
> **Eggnog said:**
> I've got Win7 and Ubuntu dual booting with EasyBCD controlling the boot through Win7.  If I "upgrade" to Win8 somewhere down the road, will it overwrite the MBR or otherwise trash my existing EasyBCD menu or will it leave it alone?  Anyone know?

I know nothing of EasyBCD, but I do know that Windows always leaves its mark in the MBR.  Expect to have to reinstall grub/mbr to get dual boot.

---

### Post by skstid2012 on 2012-11-04
Windows 8 doesn't interfere with current dual booting. It only upgrades the Windows 7 partition.

---

