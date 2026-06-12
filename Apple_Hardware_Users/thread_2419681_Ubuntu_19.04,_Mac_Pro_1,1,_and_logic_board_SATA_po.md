---
title: "Ubuntu 19.04, Mac Pro 1,1, and logic board SATA ports..."
date: 2019-05-24
forum: Apple Hardware Users
---

### Post by erll2 on 2019-05-24
so i have managed to successfully install 64-bit 19.04 on my Mac Pro 1,1... everything seems to be working fine with one exception: nothing connected to the two additional SATA ports on the logic board is registered by Ubuntu. i can boot up in macOS (10.11.6) on a SSD attached to one of those ports, and while in macOS the ODD connected to the second port shows up, so it's clearly not a hardware issue.

has anyone else run into this problem? if so, have you found a solution?

---

### Post by tangles on 2020-03-07
You have installed Ubuntu onto the disk using the MBR partition/method and so the Mac emulates BIOS. Emulated BIOS has limites... 4 SATA connectors is one of them.

You need to install Ubuntu using the GPT partion which is the EFI Firmware method. Thus no emulation and you'll see all 6 SATA ports.

Using the latter method is a bit tricky though because the MacPro 1,1 was released with 32bit EFI and all of Ubuntu's distros expect 64bit EFI.

---

