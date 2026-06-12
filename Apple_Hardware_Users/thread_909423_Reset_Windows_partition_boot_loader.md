---
title: "Reset Windows partition boot loader?"
date: 2008-09-03
forum: Apple Hardware Users
---

### Post by 3strandchords on 2008-09-03
Hi...  My last MacBook triple-boot question:

When I select to boot to the Windows partition in rEFIt, the GRUB bootloader comes up and the WindowsXP 'option' has to be selected.

Is there a way to simply have the pretty Windows icon in rEFIt boot Windows without user intervention?  

Thanks.     - 3 strand

---

### Post by cyberdork33 on 2008-09-03
By default, Ubuntu installs grub to the MBR replacing the windows boot loader. You need to install grub to the Ubuntu partition, then fix the windows bootloader by starting the recovery console and using the fixmbr command.

A similar question was asked recently and solved here:
[http://ubuntuforums.org/showthread.php?t=907262](http://ubuntuforums.org/showthread.php?t=907262)

---

