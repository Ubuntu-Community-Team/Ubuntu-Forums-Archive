---
title: "Unable to boot after running boot-repair"
date: 2013-11-28
forum: Any Other OS
---

### Post by bluestring on 2013-11-28
I am trying to dual-boot Ubuntu alongside with my pre-install windows 8 computer. However, everything time I selected Ubuntu to boot, it would give me something a message that says unable to find \NST\AutoNeoGrub0.mbr. So, I decided to run a live-cd and run the boot-repair program on it. Now it doesn't even boot. When it boots, it gives me the message No Boot disk has been detected or the disk has failed. How do I fix this? I have secured boot disabled under my BIOS.

After the first unsuccessful attempt at booting into Ubuntu, I tried re installing using another variant of linux, Linux Mint. So that is why the boot entries are Linux Mint.  [URL="http://paste.ubuntu.com/6492409/"]
http://paste.ubuntu.com/6492409/[/URL]

---

### Post by oldfred on 2013-11-29
Moved to otherOS since Mint. 

It looks like you tried wubi, but the download page for wubi clearly states it does not work with any Windows 8 pre-installed system as it uses gpt partitioning. Wubi does not work with gpt.
It also looks like you did a BIOS boot install as you now have boot loaders in the protective MBR of the gpt drive. You can dual boot with Windows in UEFI mode, and Linux in BIOS boot mode, but have to do that from UEFI menu. Once you start booting in one mode you cannot switch, so grub menu or EasyBCD will not work to switch to another install in a different mode.
When booting from UEFI menu you may have to turn on UEFI mode or BIOS/CSM/Legacy mode. Some do auto switch when you make the choice of which to boot.

It looks like Boot-Repair converted Linux install to UEFI install, added correct boot entries for Windows as your version of grub still has a bug and only creates BIOS boot entries that do not work with UEFI, and it did the "buggy" UEFI file rename. That rename is not always required and if you can directly boot ubuntu entry from UEFI menu you should undo the rename. If you can only boot Windows entry you need the rename as it has made grub be the Windows name so UEFI will boot it.

This was done:
 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi


   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by bluestring on 2013-11-29
> **oldfred said:**
> Moved to otherOS since Mint. 
This was done:
 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi


   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

After doing Boot-Repair -> Adv Options -> "Backup and rename EFI files", I get an error: unknown filesystem with a grub rescue command prompt.

---

### Post by oldfred on 2013-11-29
I said that the rename was already done & you should undo it. But I thought it would run the rename a second time, but not do anything as it sees the already renamed files.

Are you booting from a ubuntu entry in UEFI menu or the Windows entry? When renamed is done both should boot to grub. If ubuntu entry does not get you to grub menu and UEFI gives error then you need the renamed files as you have a buggy UEFI that only boots Windows.

Post new Boot-Repair.

You can also manually un-name files by changing bkpbootmgfw.efi to bootmgfw.efi. But the ubuntu boot files should all be in the /EFI/ubuntu folder.
       Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi
Then Windows entry will boot Windows from UEFI menu and ubuntu entry will boot to grub menu.

---

### Post by bluestring on 2013-11-29
I guess my question is how do I manually un-name [COLOR=#000000] /EFI/microsoft/boot/shimx64.efi ?[/COLOR]

---

### Post by oldfred on 2013-11-29
Did you try the unrename from Boot-Repair.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
[http://askubuntu.com/questions/377252/restore-backup-of-winefi-or-uefi-not-sure-that-boot-repair-made/377288#377288](http://askubuntu.com/questions/377252/restore-backup-of-winefi-or-uefi-not-sure-that-boot-repair-made/377288#377288)

User who backed up efi partition and then manually renamed files
[http://ubuntuforums.org/showthread.php?t=2131886&p=12587513#post12587513](http://ubuntuforums.org/showthread.php?t=2131886&p=12587513#post12587513)

---

