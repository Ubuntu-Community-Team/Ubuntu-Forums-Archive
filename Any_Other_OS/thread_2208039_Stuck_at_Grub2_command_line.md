---
title: "Stuck at Grub2 command line"
date: 2014-02-26
forum: Any Other OS
---

### Post by michaelfarquhar1991 on 2014-02-26
Hi, not sure I'm posting to the right place but if anyone could help I would be extremely grateful.


  After updating Windows 8 to Windows 8.1 I lost access to Grub and my  Linux Partition (running Elementary OS which is basically Ubuntu) so I tried using boot repair  from a Live USB and now I can't access either. It drops me out at some  grub command line which I don't know what to do with. All I was wanting  was the usual menu of OS's to boot into. First time round I didn't  rename the Windows efi file and when that didn't work I tried renaming  it but to no avail. The outputs from the boot repair are here: [http://paste.ubuntu.com/6999761/](http://paste.ubuntu.com/6999761/) and here: [http://paste.ubuntu.com/6999825/](http://paste.ubuntu.com/6999825/) but I don't know what any of it means.


  Even if I can just get Windows back I'd be happy but both would be fantastic.


  Thanks,

      Mike.

---

### Post by oldfred on 2014-02-26
Moved to Other OS since Elementary.

 WinEFI detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

  
Did you say yes to the rename? Best to undo unless you cannot boot the elementary entry in UEFI shown below.
Did you run rename before of after the Windows update. May be critical on what version of bootmgfw.efi Boot-Repair has in backup.

The rename is for those systems that only boot Windows from UEFI. Vendors modify systems to only boot Windows and the rename is a work around. But then you can only boot Windows from grub menu. And update will have put a new copy of bootmgfw.efi. Best not to run the undo I normally suggest as now you may have a newer version of Windows bootmgfw.efi and restore with Boot-Repair may put back the older version.

I would fully backup efi partition, and copy the latest file from Windows back into efi partition.
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)


```
 BootOrder: 0000,0001,0002
Boot0000* USB HDD:     ACPI(a0341d0,0)PCI(1d,0)USB(0,0)USB(2,0)HD(1,3e,b2cb04,000227fc)RC
Boot0001*[COLOR=#ff0000] elementary[/COLOR]    HD(2,c8800,96000,0d7a5b09-ba63-44ad-afc0-7d20bba1eab9)File(EFIelementaryshimx64.efi)
Boot0002* Windows Boot Manager    HD(2,c8800,96000,0d7a5b09-ba63-44ad-afc0-7d20bba1eab9)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................


```

Also do not know version of grub Elementary uses, but grub will not boot newer Windows 8 from grub menu with secure boot on.

---

### Post by michaelfarquhar1991 on 2014-02-26
I initially said no to rename, when that didn't work I tried again and said yes. How do you undo?

Everything has been done after Windows 8.1 update.

I know that the EFI partition is sda2 but I don't know how to access it to back it up or replace the efi file.

Secure boot is off.

---

### Post by oldfred on 2014-02-26
From liveCD or flash drive you should just be able to copy efi partition. If using Windows you have to mount the efi partition by assigning a drive letter to it. Not sure of details.

If you said yes after update to Windows this should undo it.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Or manually copy files from Windows to efi partition.

---

