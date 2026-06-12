---
title: "Boot problem"
date: 2014-08-05
forum: Any Other OS
---

### Post by luciano4 on 2014-08-05
I installed ElementaryOS Luna 64bits (ubuntu 12.04 based) on a new laptop with Windows 8. After installed, Windows 8 was still booting so I followed the common recommendation of Boot Live USB and run Boot-Repair.

Now, after that, none of both OS's are booting, and I am stuck in the GRUB screen "Minimal BASH-like line editing is supported...". The only thing I can do is boot again from LiveUSB and run Boot-Repair (I did it a couple of times).

This is the Paste2 url it throw: [http://paste2.org/k1G1yI7L](http://paste2.org/k1G1yI7L)


Please help.

---

### Post by oldfred on 2014-08-05
Moved to Other OS since not Ubuntu.

What system & model is this. And what video chip?

You may be better served with a newer version. Linux software takes months or even year or two to catch up with new hardware. If system is new and UEFI based, then the newest version of Ubuntu will work better as it has newer Kernel, support software and video drivers.

You show grub installed to the MBR for BIOS boot, but also grub in efi partition for UEFI boot. Did you use Boot-Repair to convert the BIOS install to UEFI?

You also show this which is why Windows will not boot when in UEFI mode.
       /EFI/Microsoft/Boot/bkpbootmgfw.efi 

and in grub menu:
      
 menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 7C15-5959
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

That is because many systems partitcularly HP & Sony only boot the UEFI entry with Windows. So it copyies grub or shim into the Windows efi Boot folder and renames it to bootmgfw.efi and renames the original Windows file. Then you can only boot Windows from the grub menu using the bkpbootmgfw.efi file.

Better to undo the rename, you then should be able to boot Windows in UEFI mode from UEFI menu.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
[http://askubuntu.com/questions/377252/restore-backup-of-winefi-or-uefi-not-sure-that-boot-repair-made/377288#377288](http://askubuntu.com/questions/377252/restore-backup-of-winefi-or-uefi-not-sure-that-boot-repair-made/377288#377288)

    
Do you get to grub menu or just grub> or grub rescue>  ?

---

### Post by luciano4 on 2014-08-05
My Windows 8 works again. Was fixed by ticking the "Restore EFI backups"
The Elementary OS, still throwing GRUB error.


As for your questions:
- My laptop: ASUS N56VB (i7, ram 8GB, video card nvidia 740m) 
- Just grub> *(screen: [http://s27.postimg.org/6n0oq8fb7/grub.jpg](http://s27.postimg.org/6n0oq8fb7/grub.jpg))*



Thanks!

---

### Post by oldfred on 2014-08-05
Is it dual video or just the nVidia? With nVidia you will need the nomodeset  boot option and add that to the linux line in the grub menu. But you need to get to grub menu first.

It seems like some part of grub is not installed correctly.
Boot-Repair's advanced options has a full uninstall and reinstall of grub. I might try that first.  Be sure to boot Boot-Repair in UEFI mode and best to use same version of Ubuntu/Elementary as your install.
It is a chroot and  purge of old grub and total new install of grub, but makes it a bit easier as it walks you thru it.

Some possibly similar Asus.
 Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
      
 HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

---

### Post by luciano4 on 2014-08-06
I tried to do what you commented me but I didn't make it. When I add the "nomodeset" to the linux line in grub menu, after saving it, the screen remains black.


On the other hand I have both OS's again with GROW error. It happened again in Win 8 after tick the option "purge grub before reinstalling it" in Boot Repair (I did this just to test). But now I can't get Win8 running again 


help :( 
Thanks again.

---

### Post by oldfred on 2014-08-06
Did Boot-Repair do the rename again?
Otherwise you should always be able to boot Windows from UEFI menu. Or you have separate unrelated Widnows issues.

Post new link to new run of BootInfo report.

---

### Post by luciano4 on 2014-08-06
Yes, i ticked again the "Restore EFI backups" option of Boot-Repair.

This is the new link: [http://paste2.org/CWDx0msA](http://paste2.org/CWDx0msA)

---

### Post by oldfred on 2014-08-06
As long as you have this it is the real Windows efi file. Not sure if then  bootmgfw.efi is now Windows or grub?

/EFI/Microsoft/Boot/bkpbootmgfw.efi

Just to make sure Boot-Repair restored the correct file.
       Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

From live installer you should be able to mount the Windows drive as long as you did not leave it hibernated (fastboot). Then drill down and find the bootmfgfw.efi and copy into /EFI/Microsoft/Boot folder in the efi partition.

---

