---
title: "Internal XP, External Ubuntu"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-08-05
Hello,
I've successful installed an external boot of Ubuntu 7.04 with Windows xp on the internal IDE.  

However, I have to have the external (ubuntu) hd attached untill I get to the menu.lst boot menu, or else I get a Grub error22  (If I have any other hard drives attached during boot, I get a grub error 17).  The error 17 doesn't have an impact, but the error 22 can be annoying because this means if I want to boot up the laptop in, for example, a cafe, I'll need to lug in the external hard drive!

Any ideas on how to allow the normal xp boot sequence without the external hd (and still keeping the dual-boot)?  

Thanks.l

(Note: Someone mentioned that my grub sequence may need the external ubuntu hd "to play" -- to check to see if it's there for some reason.  But really, shouldn't BIOS handle the early stages of boot and only resort to grub in the case of booting to ubuntu?)

---

### Post by logos34 on 2007-08-05
You need to restore windows bootloader to the MBR of the internal drive (using the windows install cd>recovery console>'fixboot') and then either (re)install grub to the external usb drive, or boot ubuntu from windows bootloader (not all that hard to do)

---

### Post by ugm6hr on 2007-08-05
There are a variety of solutions - I have given one here:

Boot into Ubuntu.
Install ntfs-3g & ntfs-config from Synaptic Package Manager, then run NTFS configuration tool (in System Menu) to allow read/write access to XP.
Copy /boot/grub/menu.lst to your Windows C:\ (whatever it is called in Ubuntu - probably /media/Disk1 or something like that) so that it appears as C:\menu.lst from within XP.

Download GRUB4DOS and put it in the Windows C:\ as well:
[https://sourceforge.net/projects/grub4dos](https://sourceforge.net/projects/grub4dos)

Then follow this (just the bit for NT/2000/XP/2003):
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager)
You can make the command more approprite, e.g. *C:\grldr="Ubuntu"*
Editing boot.ini from XP is not that straightforward - from memory  - you need to go to Control Panel, open System (somewhere in Performance / Maintenance) - click Advanced tab - Startup and Recovery "Settings" - System Startup "Edit"

Follow the advice here:
[http://ubuntuforums.org/showpost.php?p=3080193&postcount=8](http://ubuntuforums.org/showpost.php?p=3080193&postcount=8)
If the download doesn't work - try here: [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx) (or google mbrfix for other alternatives)
PS: Don't worry that it mentions deleting Ubuntu - that part is irrelevant.  [COLOR="Red"]But only follow steps 1-6[/COLOR]

Hopefully, you should now have a fully functional dual-boot, with XP as the default.  If you ever update the kernel in Ubuntu - you will have to manually update C:\menu.lst (probably just copy it from /boot/grub/menu.lst again).

---

### Post by logos34 on 2007-08-05
> Boot into Ubuntu.
Install ntfs-3g & ntfs-config from Synaptic Package Manager, then run NTFS configuration tool (in System Menu) to allow read/write access to XP.
Copy /boot/grub/menu.lst to your Windows C:\ (whatever it is called in Ubuntu - probably /media/Disk1 or something like that) so that it appears as C:\menu.lst from within XP.

Download GRUB4DOS and put it in the Windows C:\ as well:
[https://sourceforge.net/projects/grub4dos](https://sourceforge.net/projects/grub4dos)

Then follow this (just the bit for NT/2000/XP/2003):
[http://grub4dos.sourceforge.net/wiki...3_boot_manager](http://grub4dos.sourceforge.net/wiki...3_boot_manager)
You can make the command more approprite, e.g. C:\grldr="Ubuntu"
Editing boot.ini from XP is not that straightforward - from memory - you need to go to Control Panel, open System (somewhere in Performance / Maintenance) - click Advanced tab - Startup and Recovery "Settings" - System Startup "Edit"

This is the way to go if you decide to use windows bootloader (it's what I have setup on my machine--with a slight modification) although I ordinarily use grub to boot.  

All you have to do to call up boot.ini in windows is type in the address bar:
**C: \boot.ini**

---

