---
title: "rEFIt + grub = half way working?"
date: 2007-10-25
forum: Apple Intel Users
---

### Post by digitalchaos on 2007-10-25
I am triple booting with OSX Leopard, Win XP, and Ubuntu 7.10.
rEFIt is showing me 3 choices which is good. The problem is that both the Windows and Linux choices in rEFIt send me to the grub bootloader to chose either ubuntu or windows. Thats not exactly how it should be working. Any help?  I understand that 7.10 fixed the issues with grub being incompatible with EFI and that certainly seems to be true. I think the case here is a simple configuration issue with grub.

Also, for what it is worth Leopard does not give you the ability to make a partition with the "Linux" file type anymore. I had to create it as an MS-DOS partition and then boot off the Ubuntu CD and change the ID to Linux and format it with ext3. This was all done before throwing windows on the laptop and then finally Ubuntu.

---

### Post by cyberdork33 on 2007-10-25
> **digitalchaos said:**
> I am triple booting with OSX Leopard, Win XP, and Ubuntu 7.10.
rEFIt is showing me 3 choices which is good. The problem is that both the Windows and Linux choices in rEFIt send me to the grub bootloader to chose either ubuntu or windows. Thats not exactly how it should be working. Any help?  I understand that 7.10 fixed the issues with grub being incompatible with EFI and that certainly seems to be true. I think the case here is a simple configuration issue with grub. actually that was all fixed in feisty. You have replaced the windows bootloader with grub, thus it is launched not for linux and windows. you can install grub to the ubuntu partition (instead of the deafult MBR location).
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

then boot the windows cd into recovery mode, and use fixmbr to reinstall the windows bootloader there.

> Also, for what it is worth Leopard does not give you the ability to make a partition with the "Linux" file type anymore. I had to create it as an MS-DOS partition and then boot off the Ubuntu CD and change the ID to Linux and format it with ext3. This was all done before throwing windows on the laptop and then finally Ubuntu. you can also just use the installer to delete the entire partition, then tell it to use the free space.

---

### Post by digitalchaos on 2007-10-25
> **cyberdork33 said:**
> actually that was all fixed in feisty. You have replaced the windows bootloader with grub, thus it is launched not for linux and windows. you can install grub to the ubuntu partition (instead of the deafult MBR location).
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

then boot the windows cd into recovery mode, and use fixmbr to reinstall the windows bootloader there.

That was the fix, thanks! What should I have done differently to avoid doing this fix though? I would rather not make this a frequent thing if it isn't needed.

> 
 you can also just use the installer to delete the entire partition, then tell it to use the free space.
I was running into issues where where windows would refuse to boot after the first step of the CD install when both the 3rd and 4th partitions were FAT for some reason. Thats the only reason I did this extra step. This may have ultimately been related to the boot loader though.

---

### Post by cyberdork33 on 2007-10-25
> **digitalchaos said:**
> That was the fix, thanks! What should I have done differently to avoid doing this fix though? I would rather not make this a frequent thing if it isn't needed.On the live cd installer, just before you confirm stuff and click install, there is an advanced button where you can set where to install grub.

---

