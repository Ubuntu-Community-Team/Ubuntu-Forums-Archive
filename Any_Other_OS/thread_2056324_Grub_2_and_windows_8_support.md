---
title: "Grub 2 and windows 8 support"
date: 2012-09-11
forum: Any Other OS
---

### Post by mcstat on 2012-09-11
Has GRUB 2 now got Windows 8 support, I'm scared to install Windows 8 and not be able to boot to Linux?

---

### Post by mips on 2012-09-11
See if there is anything of use in here [http://ubuntuforums.org/showthread.php?t=2055842](http://ubuntuforums.org/showthread.php?t=2055842)

Dunno if any of it applies to opensuse

---

### Post by tienlbhoc on 2012-09-11
install win8 first and install ubuntu after.

or fix grub2 with ubuntu cd(google please)

---

### Post by oldfred on 2012-09-11
Current installs of Windows 8 are similar to Windows 7. But depending on your system may be UEFI/gpt or BIOS/MBR. 

Only new systems built by vendors will automatically have the UEFI security bit turned on. Not sure what they will do with any other installs. But user has the capability to turn secure bit off, which probably is the easiest solutions. But not politically easy to sell the idea that turning off "Security bit" makes sense.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

