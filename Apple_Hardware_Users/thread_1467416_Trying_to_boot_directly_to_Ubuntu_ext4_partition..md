---
title: "Trying to boot directly to Ubuntu ext4 partition."
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by god720 on 2010-04-30
I am dual booting Ubuntu 9.10 with ext4 and OS X with hfs+, and I'm getting tired of having to go through Open Firmware, rEFIt, and GRUB to boot to Ubuntu by default. I've done a lot of digging, and my results appear to be inconclusive. I have, however, been able to hypothesize that the reason that I cannot set my ext4 partition as the Startup Disk (via OS X settings) is because OS X does not know how to read ext4. I believe that the Startup Disk settings work by writing to Open Firmware, so I'm thinking that maybe something else would be able to as well, preferably something that is capable of reading ext4. Can anyone help in this regard?

---

### Post by srs5694 on 2010-04-30
I can't really help you with specifics, but I think you're bound to be confused because of an inconsistency in your beliefs about your system. Specifically, Open Firmware was used on PowerPC-based Macs, but is no longer used on Intel-based systems. Intel-based computers use the Extensible Firmware Interface (EFI), and rEFIt is an EFI boot loader. Thus, either you've got an older PowerPC-based Mac, in which case you've got Open Firmware, making rEFIt and all other EFI information meaningless; or you've got a newer Intel-based Mac, in which case you've got EFI and all Open Firmware information you may have found is irrelevant. If you're not sure what you've got, select "About This Mac" in OS X or type "cat /proc/cpuinfo" in a Linux shell; both methods will tell you what sort of CPU you've got.

---

### Post by god720 on 2010-04-30
Yeah sorry it's EFI. I read Open Firmware somewhere and didn't really think about it. Regardless, replace every instance of Open Firmware in my original post with EFI.

---

