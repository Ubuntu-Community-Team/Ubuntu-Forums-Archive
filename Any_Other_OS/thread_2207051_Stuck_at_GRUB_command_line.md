---
title: "Stuck at GRUB command line"
date: 2014-02-21
forum: Any Other OS
---

### Post by caleb6 on 2014-02-21
Hey all, I'm have recently installed elementaryOS (based on Ubuntu 12.04) however matter what I try I always end up with the same empty grub prompt at boot regardless of which OS I choose to boot into with my BIOS. (My other OS is windows 8)

ive tried boot-repair countless times but never seem to make any progress. I'll provide the link it gave me for my latest attempt:

[http://paste.ubuntu.com/6973975/](http://paste.ubuntu.com/6973975/)

any help at all would be very much appreciated!

---

### Post by oldfred on 2014-02-22
Moved to OtherOS since not Ubuntu.

If looks like Elementary has the older version of grub that os-prober does not correctly create Windows boot entries. It still creates BIOS type that will not work with UEFI.

Then only entries from Boot-Repair will work, but you have done the 'buggy' UEFI fix that may or may not be required. But with the fix you can only boot Windows from grub menu with bkpbootmgfw.efi file as the renamed actual Windows file. From UEFI both elementary & Windows entries will give you grub menu.

Best to undo rename and see if system boots. It will then boot Windows from UEFI menu if Windows is not otherwise corrupted. But you need Windows repair tools if it does not boot. You do have a Windows 8 repair flash drive?

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.
Then from UEFI menu with secure boot on or off Windows should boot.
But Elementary does not have secure boot versions of grub nor kernel and will not boot with secure boot on.

If Windows does not boot, you need to have made this first. Or have someone else with Windows 8 that you know.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by caleb6 on 2014-02-22
Thanks for the reply, I really appreciate it!

Unfortunately I don't have my other windows 8 machine accessible at this time to make a repair USB. I won't be able to until sometime next week. Is there any set of instructions I can follow to make elementary bootable for now?

---

### Post by oldfred on 2014-02-22
If you boot elementary from UEFI what do you get. 
Grub menu, or grub rescue command line? Or error by UEFI on no bootable system?

If grub rescue does this work?
 configfile (hd0,gpt8)/boot/grub/grub.cfg

---

### Post by caleb6 on 2014-02-22
Computer boots, I see a couple errors thrown up real fast too fast to read, then a brief flash of static then the grub command line (no rescue)

lemme try to read it I'll see if I can figure out what it says

---

### Post by caleb6 on 2014-02-22
This is exactly what I get:
[[img]http://s16.postimg.org/8pbougu9d/image.jpg[/img]](http://postimg.org/image/8pbougu9d/)
Followed immediately by
[[img]http://s27.postimg.org/cuu46z9mn/image.jpg[/img]](http://postimg.org/image/cuu46z9mn/)

---

### Post by oldfred on 2014-02-23
Can you boot the Windows entry in UEFI?
Do you have secure boot on? Then only secure boot systems are allowed to boot.

And it looks like you have run the 'buggy' UEFI rename which Boot-Repair does for those systems that modify UEFI to only boot Windows. Then when you boot Windows from UEFI menu, you get grub menu, but then can only boot Windows from grub menu as it has been renamed to bkpbootmgfw.efi.

Try undoing the rename and see if Windows still boots.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by caleb6 on 2014-02-23
Ok thank you I'll try that as soon as I can make another USB disk

---

