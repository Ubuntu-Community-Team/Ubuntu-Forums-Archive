---
title: "Mavericks and Ubuntu?"
date: 2013-10-23
forum: Apple Hardware Users
---

### Post by petersphilo on 2013-10-23
Hello All,
it seems Mavericks refuses to install on a drive that does not have a GUID partition table..
However Ubuntu needs Master Boot Record partition scheme...

Has anyone encountered this?
any advice (aside from using separate drives?

Thank you

---

### Post by coffeecat on 2013-10-23
> **petersphilo said:**
> However Ubuntu needs Master Boot Record partition scheme...


I don't have any experience of dual-booting MacOS and Ubuntu, so I can't give you specific installation help, but I thought I'd pick this point up. That is not correct. Ubuntu can install to and boot up from a disc with a GPT (GUID partition table). It has been able to for far longer than Windows.

---

### Post by entangled on 2013-10-24
ubuntu install DVD is not recognized on my iMac, running from gpt disk with protective MBR. A ubuntu USB stick IS recognized but does not complete install due to inability to deal with disk layout (needs EFI partition, but not the one I have). The only way I have gotten linux to install dual boot on my iMac is to use an Archboot CD (not Arch; that fails). Archboot recognizes, and uses, the disk layout. I think other mac users may not need to do this, but my iMac is apparently fussy. Even then dual boot is unsatisfactory because my radeon graphic card is not supported (I have to use slow fbdev driver) and suspend- resume (essential to me) is not working. Arch runs very well (ubuntu not so well) in virtualbox on iMac.

---

### Post by petersphilo on 2013-10-25
> **coffeecat said:**
> Ubuntu can install to and boot up from a disc with a GPT (GUID partition table).

i have to say that this hit me like a ton of bricks!
i hope it's true!
i'm going to try it this Week End.. First i have to backup the 500GB of crap i have on my primary drive, switch back to GUID scheme, dump the 500GB back onto it, and then try to install 13.10 ...

Be Well All!!

---

### Post by coffeecat on 2013-10-25
> **petersphilo said:**
> 
i hope it's true!

It's true all right! Somewhat irrelevant to your project, this wiki page describes setting up Ubuntu on the newer UEFI PCs, which essentially means having a GPT:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> **petersphilo said:**
> i'm going to try it this Week End.. First i have to backup the 500GB of crap i have on my primary drive, switch back to GUID scheme, dump the 500GB back onto it, and then try to install 13.10 ...

Good luck. You may find these pages helpful:

[https://help.ubuntu.com/community/DualBoot/MacOSX](https://help.ubuntu.com/community/DualBoot/MacOSX)

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

[http://refit.sourceforge.net/](http://refit.sourceforge.net/) (for information - rEFit is no longer maintained)

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

The first two links are in need of some updating perhaps, so I don't know whether Mavericks will spring any surprises on you.

---

