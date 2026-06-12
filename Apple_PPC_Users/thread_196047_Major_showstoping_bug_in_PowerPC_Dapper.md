---
title: "Major showstoping bug in PowerPC Dapper"
date: 2006-06-13
forum: Apple PPC Users
---

### Post by Hiroshi on 2006-06-13
> The 2.6.15 kernel fails to boot on Dapper. The boot process appears to stop with the lines:

"loading ramdisk
Ramdisk loaded at 01900000, size: 4625 Kbytes"

When booted with "linux debug" at the yaboot prompt, the same thing happens, but the the added effect of the monitor turning off after the line "Ramdisk loaded at 01900000, size: 4625 Kbytes" is displayed.

This seriously needs to be addressed guys, I've finally got ahold of Breezy, so I can get Linux running on my G3.. 

[Source]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

---

### Post by colinhayes on 2006-06-14
[QUOTE=Hiroshi]This seriously needs to be addressed guys, I've finally got ahold of Breezy, so I can get Linux running on my G3.. 

[Source]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")[/QUOTE]

yes, it's a bug labeled highly critical assigned to Ben Collins—it'll get fixed.

---

### Post by nkbj on 2006-06-15
The fixes kernel (2.6.15-25) has hit the update repositories.

---

### Post by avtolle on 2006-06-15
Updated kernel about 2 hours ago, along with 51 other updates. All seems well to this point with my "vanilla" cube. Hopefully, this will take care of the various problems that others have had.

---

### Post by RaSa on 2006-06-18
Hello!

I downloaded the LiveCD and alternative install CD from a german mirror today (Sunday, June, 18, 2006). And that error is still there.

Both stop just after loading the ramdisk on my iMac G4 TFT as described above.

Where can I get a fixed version for shure?

Thank's in advance,

Ralf

---

### Post by nkbj on 2006-06-18
Unfortunately they have not released a fixed CD. Your best option is to install breezy and then do a dist-upgrade.

---

