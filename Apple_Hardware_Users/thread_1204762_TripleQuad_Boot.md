---
title: "Triple/Quad Boot?"
date: 2009-07-05
forum: Apple Hardware Users
---

### Post by Ecstatic23 on 2009-07-05
I'm buying a 13" 2.26GHZ Macbook Pro with 4gb DDR3 RAM and 500GB HDD,

I wish to boot OS X/Ubuntu 9.04/Windows XP and maybe 7 when it comes out.
I already have XP and Jaunty burnt on to USB's.

When I receive the MacBook, what do I have to do to install them?

---

### Post by tiagobt on 2009-07-05
There's a Wiki page explaining how to install Ubuntu on Intel Macs:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Look for the section that explains how to install Mac OS X + Ubuntu + Windows XP. I have never installed Windows 7, so I'm not sure the same instructions apply.

Also, consider installing Ubuntu from a CD, not a USB stick. The installation from USB sticks is much harder and is still experimental.

---

### Post by hajk on 2009-07-06
Triple or even quad booting? Not without a bit of effort and understanding of the problems surrounding the EFI replacement of the BIOS used by Apple.

In principle, you should be able to boot any number of OS'es via an EFI boot loader, but only in principle. Grub-efi, for example, has come a long way but isn't quite ready for prime time yet (there is a lengthy and active thread on that here). So, that leaves booting OS'es other than Mac OS X via the old legacy MBR method... which can only be done from one of the partitions numbered 1..4. Since EFI and Mac OS X already occupy partitions 1 and 2 out-of-the-box, you would first have to move those partitions to numbers > 4 before you could consider booting three or four "legacy" OS'es.
Having said that, I doubt whether DiskUtil in Mac OS X will even allow you to move that EFI partition from first spot, so that would leave at most three bootable legacy OS'es, as things stand now.

---

### Post by Ecstatic23 on 2009-07-06
> **tiagobt said:**
> There's a Wiki page explaining how to install Ubuntu on Intel Macs:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Look for the section that explains how to install Mac OS X + Ubuntu + Windows XP. I have never installed Windows 7, so I'm not sure the same instructions apply.

Also, consider installing Ubuntu from a CD, not a USB stick. The installation from USB sticks is much harder and is still experimental.

Damn, could you please explain that for me if I was just to go for OS X/XP/Ubuntu?

I'm no expert at any of this.

---

