---
title: "Can't Boot Automatically into Linux"
date: 2014-05-08
forum: Any Other OS
---

### Post by Kris_Pennington on 2014-05-08
I installed Linux Mint and wiped drive instead of dual boot. After the installation I restarted but now the only way to boot into Linux is if I spam Esc to be able to go into boot options and select it from there. After that it then takes me into the GRUB menu then I can select to boot into Linux which finally boots into Linux. How can I make it to where either GRUB pops up automatically or it just boots into Linux automatically? Currently if I don't click anything it says there is not any bootable image. Please help I've looked everywhere.

---

### Post by kc1di on 2014-05-08
It sounds like you have a secure Boot /UEFI.  machine.  and even though you formatted the disc  The bios is still set to UEFI.
If you can get to the setup page their should be a setting call legacy boot. (or something similar) disable secure boot and enable legacy and that should solve your problem

If you desire to keep secure boot you may want to run boot-repair. you can get it[ here.]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Kris_Pennington on 2014-05-08
When I turn off Secureboot and switched to Legacy it says no OS installed.

---

### Post by kc1di on 2014-05-08
did you run boot-repair ?

---

### Post by Kris_Pennington on 2014-05-11
Yeah I ran boot-repair which fixed the problem but now when I press F9 to select boot options (just to check if it worked the grub menu does come up automatically) it lists ubuntu ALOT. Look [here]("http://i.imgur.com/vWVtrVx.jpg").

---

### Post by oldfred on 2014-05-11
Moved to OtherOS since Mint.

You may want to use efibootmgr to houseclean UEFI entries.

       Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by Kris_Pennington on 2014-05-11
Alright thanks I fixed it. I'll change the thread to solved.

---

