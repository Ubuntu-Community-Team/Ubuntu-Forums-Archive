---
title: "UEFI boot Lenovo G480 laptop"
date: 2014-03-15
forum: Any Other OS
---

### Post by marcelotf2 on 2014-03-15
[COLOR=#000000][COLOR=#000000][FONT=Verdana]I'm having the same error: "efidisk read error" after trying boot-repair. Here is how that happened:[/FONT][/COLOR][COLOR=#500050]
[COLOR=#000000][FONT=Verdana]I have a Lenovo G480 laptop that came with Windows 8 pre-installed, after 1 year of use I decided to try linux because my system was getting too messy and slow, so I chose elementary os luna, made a usb stick bootable with it, changed from UEFI to Legacy in BIOS options, and booted it, created some partitions and installed, everything running fine, restarted it and it showed me a nice grub interface where I could select 4 options: "elementary OS, elementary OS secure mode, windows recovery environment, windows 8 (loader)" so when I tried to boot windows 8 it failed, this was because it was still in legacy.[/FONT][/COLOR]

[/COLOR]
[COLOR=#000000][FONT=Verdana]When I changed back to UEFI mode in BIOS, it started loading Windows 8 right away (no grub showed up), I took that chance to turn off the Fast Startup from Win8 and then turned off the laptop. Turned on again, changed back to Legacy mode and started elementary. Then I thought the reason I couldnt see GRUB was because I had installed elementary in legacy mode while win8 is in uefi mode, with that in mind I decided to convert eOS to UEFI, following this tutorial: [/FONT][/COLOR][FONT=Verdana][https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode) , I did exactly what it shows there and it returned this link in the end: [/FONT][COLOR=#000000][FONT=Verdana][http://paste.ubuntu.com/7096745/](http://paste.ubuntu.com/7096745/)

When I restarted the system, I changed back to UEFI, but then I got an error: "Windows boot manager has been blocked by the current security policy" 3 times in the screen and then it started loading the OneKey Recovery interface that comes with Lenovo laptops. I restarted it again and disabled "secure boot" in BIOS settings, then got that error: "efidisk read error", and then it stops at grub prompt (grub>). Changed back to legacy mode, booted again, and I got "error: invalid arch independent elf magic" (what a funny error btw) stopping at grub prompt (grub rescue>), so now it doesnt boot in any way.

[/FONT][/COLOR][FONT=arial][COLOR=#000000]As a last try to fix it, I booted with usb stick and tried once again Boot Repair, but this time I only clicked the "Recommended fix" button, which in the end gave me this link: [/COLOR][/FONT][http://paste.ubuntu.com/7097055]("http://paste.ubuntu.com/7096745/")/ , but I still have the same errors.
[FONT=arial]
So, is there any way I can fix it? 
BTW, sorry for the long post and thanks for taking your time to read it.[/FONT][/COLOR]

---

### Post by oldfred on 2014-03-16
Moved to your own thread as now issues are different. 

I now looks like Boot-Repair converted install to UEFI boot mode. So grub installed in MBR will not boot in BIOS boot mode and just give errors. Only boot in UEFI boot mode with secure boot off.
Can you boot elementary boot entry from UEFI menu? If so turn off 'buggy' UEFI fix. That is only for those systems that only boot Windows entry in UEFI menu. Both Windows & elementary entry should boot to grub.
With the 'buggy' UEFI rename, you can only boot Windows from grub menu.

 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

If you even get grub> or grub rescue you do not need rename as you are booting the Ubuntu entry. If you get a UEFI error even with secure boot off of not authorized then you may need the rename.

Other Lenovos which may be similar, even if different models.

 Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

---

### Post by marcelotf2 on 2014-03-16
Well, after reading many things and deciding what to do, hours ago I decided to reinstall elementary, but this time I turned **Secure Boot OFF** and set it to **UEFI** instead of **Legacy** before installing.

So I only formatted the root partition of eOS and installed it again, when it finished and rebooted I got 3 entries in the UEFI menu:[INDENT][I]- elementary (ST1000LM024 HN-M101MBB)
- Windows Boot Manager (ST1000LM024 HN-M101MBB)
- Windows Boot Manager (ST1000LM024 HN-M101MBB)[/I][/INDENT]

if I select "elementary (ST1000LM024 HN-M101MBB)" option I get to the grub menu with the 5 following options:[INDENT][I]- elementary OS, with Linux 3.2.0-51-generic
- elementary OS, with Linux 3.2.0-51-generic (recovery mode)
- Windows Recovery Environment (loader) (on /dev/sda3)
- Windows 8 (loader) (on /dev/sda5)
- System setup[/I][/INDENT]

if I select "elementary OS, with Linux 3.2.0-51-generic" option, it works, and I can boot the system properly 

if I select "Windows Recovery Environment (loader) (on /dev/sda3)" or "Windows 8 (loader) (on /dev/sda5)" I get the following error:[INDENT][I]error: unknown command 'drivemap'.
error: invalid EFI file path.
press any key to continue ...[/I][/INDENT]

and finally, if I select any of the two "Windows Boot Manager (ST1000LM024 HN-M101MBB)" options in the UEFI menu, I get the "efidisk read error" with the grub prompt "grub>"

Any ideas?
BTW, I just generated another BootInfo link:  [http://paste.ubuntu.com/7104154/](http://paste.ubuntu.com/7104154/) , no more fixes were attempted yet.

---

### Post by oldfred on 2014-03-16
Old versions of grub have a bug in the os-prober. Those only create BIOS boot entries that do not work with UEFI. You have to manually create correct entry to chain to Windows in efi partition or Boot-Repair can auto create a new entry in 25_custom. As long as os-prober is wrong you can even turn it off for now to eliminate the incorrect entries. Details on that in link in my signature.

         grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry from os-prober that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

Did you run the rename with Boot-Repair. Undo it so Windows will work from UEFI menu.

 It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

You may need to use efibootmgr to remove duplicate entries in UEFI.

---

### Post by marcelotf2 on 2014-03-16
> **oldfred said:**
> Old versions of grub have a bug in the os-prober.

The version of GRUB that shows up in menu is 1.99-21ubuntu3.14, does this one also has that bug? 


> **oldfred said:**
> Did you run the rename with Boot-Repair. Undo it so Windows will work from UEFI menu.

Yes, I believe I clicked in the "YES" option when Boot Repair asked me "Do you want to activate [Backup and rename Windows EFI files]?"


> **oldfred said:**
> To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.


I don't think I can do that anymore, unless Boot Repair store the EFI backup anywhere at /home partition, because the main partition was formatted so I could install elementary again.

EDIT: Actually, I decided to try the Restore Backup option anyway and It solved it, now I can boot from "Windows Boot Manager (ST1000LM024 HN-M101MBB)" option in the UEFI menu again.

But the "Windows 8 (loader) (on /dev/sda5)" still doesnt work, I have to do that fix you mentioned, but Im still figuring out how to do it.

EDIT2: Forgot to post the link:  [http://paste.ubuntu.com/7104819/](http://paste.ubuntu.com/7104819/)

---

### Post by marcelotf2 on 2014-03-16
> **oldfred said:**
> As long as os-prober is wrong you can even turn it off for now to eliminate the incorrect entries. Details on that in link in my signature.

I finally come with this solution from your tutorial:
[COLOR=#000000]$ sudo bash -c "echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub"[/COLOR]
[COLOR=#000000]$ sudo update-grub
[/COLOR]
And it's fixed now! Removed the 2 non working entries from GRUB. If I want to boot windows I can do it by the EFI Menu, Its ok, I dont mind that.

Thank you oldfred! :D

---

### Post by oldfred on 2014-03-16
Glad it is working.

Boot-Repair should be able to add an entry to grub menu to chain back to the Windows efi file. Or you can manually add one to 40_custom. See bug report for examples.
But you should be able to boot with one time boot key or from UEFI menu anytime.

---

