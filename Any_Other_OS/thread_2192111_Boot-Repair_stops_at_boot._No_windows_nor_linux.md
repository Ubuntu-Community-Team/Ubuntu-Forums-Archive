---
title: "Boot-Repair: stops at boot. No windows nor linux"
date: 2013-12-06
forum: Any Other OS
---

### Post by dvddvd on 2013-12-06
[http://paste.ubuntu.com/6528264/](http://paste.ubuntu.com/6528264/)

New computer with Windows 8. Installed Linux Mint 15 KDE as dualboot.
Restarted but only reloaded in Windows.
Via liveCD ran Boot-Repair.
Now computer stops at boot. No windows, no linux. Only restarts from DVD into liveCD.

Anybody that knows what's happening?

---

### Post by oldfred on 2013-12-06
Moved to other OS.

I would suggest undoing the rename until we know if you system only boots Windows.

       It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.

   
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.
Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

     
Have you turned off secure boot?

LIne 1132, but it always shows several different one's and I am not sure of difference. One may be secure boot on, as that will only boot secure boot installs. You do show signed kernels, so mint should even boot with secure boot on.
 BootCurrent: 0006
Timeout: 0 seconds
BootOrder: [COLOR=#ff0000]0002[/COLOR],0003,0006,0000,0001
Boot0000* P0: WDC WD10EZEX-75ZF5A0      	BIOS(11,0,00)
Boot0001* P4: TSSTcorp DVD+/-RW SH-216CB	BIOS(13,0,00)
Boot[COLOR=#ff0000]0002[/COLOR]* linuxmint	HD(1,800,fa000,fca6164a-9cbe-4efe-995f-00b9c0563c7e)File(EFIlinuxmintshimx64.efi)
Boot0003* Windows Boot Manager	HD(1,800,fa000,fca6164a-9cbe-4efe-995f-00b9c0563c7e)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...................
Boot0006* UEFI: TSSTcorp DVD+/-RW SH-216CB	ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000CD-ROM(1,a4d54,11c0)AMBO

This shows you have linuxmint as boot option, but if your system does not boot that entry, then because of the rename the 0003 entry is currently really shim so you should get grub menu.

But full booting of a Linux may not be UEFI/grub but video or other issues. what video card?
Did you run the update to Boot-Repair before running it? It now shows video card/chip.

I normally do not suggest separte /boot for most desktop installs.

Remove medibuntu from sources. That is nomore.

 Medibuntu discontinued April 2013
[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)
[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

---

### Post by dvddvd on 2013-12-06
I'm pretty profient with computers, but the whole boot thing still amazes me. 
This info doesn't help me much. In the meantime reinstalled win8, used mint 16 cinnamon with boot-repair. First restart shows complete grub, but after rebooting twice in windows 8, no more grub, only windows.
Probably loose the windows thing entirely or reinstalling thru vmware.
Thanks for the help.

---

