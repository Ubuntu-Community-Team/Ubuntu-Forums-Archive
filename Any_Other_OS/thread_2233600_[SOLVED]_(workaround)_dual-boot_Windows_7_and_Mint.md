---
title: "[SOLVED] (workaround) dual-boot Windows 7 and Mint 17 w/ UEFI BIOS"
date: 2014-07-09
forum: Any Other OS
---

### Post by Some_Old_Programme on 2014-07-09
I got a new machine for my birthday; having cut over from XP on my previous machine, I determined to primarily use a Linux distro, while keeping the as-delivered Windows 7 alive to be able to easily update BIOS and optical drive firmware.

Things went pretty well, although I'd never dealt with an UEFI boot disk before. Just before wrapping up, though, my dual boot tests failed disastrously. Windows seemed to wipe out the ability to boot Mint (the distro I chose).

A few details that I belive to be relevent: the BIOS are American Megatrends version 80.15 on an HP 500-281 box.

After installing Mint, the box would boot into grub2 menu that included the Windows 7 partition as a choice. So far so good. After choosing to boot into Windows 7, then shutting down, the next bootup would go directly into Windows. Getting into the BIOS boot device menu (in this case, pressing <ESC> early in the powerup sequence, then using an F<#> key to get to the boot device menu) showed the Mint partition as a boot choice, but selecting it failed with an alarming message (something to the effect of no system on the partition). Booting my Mint flash drive showed that the message was wrong--there most certainly was a system on that partition.

I went many rounds trying to fix the problem, including using Boot-Repair (seemed to fix the problem, only to have it recur once I'd booted into Windows 7). I finally reinstalled Mint and took a snapshot backup of the UEFI partition to try to toubleshoot what was getting modified by booting into Windows. The answer, bafflingly, seemed to be nothing.

The problem: the BIOS boot order is getting rearranged by booting into different systems. I don't believe that this is either a Linux or Windows problem, but a bug in the BIOS.

Workaround: after booting into Windows and shutting down, I need to go into BIOS configuration (NB: *not* the boot device menu) and change to boot order to move ubuntu partition up before Windows. Note, also, that after booting into Mint, the Windows partition disappears as a choice from the BIOS boot menu, but is accessable from the grub2 boot menu.

---

### Post by hbutt875 on 2014-07-09
my advise is to log in into windows format or delete the linux mint partion.If you delete the partition then recreate it. Now install ubuntu (supported version).Boot from cd,dvd or usb. Install the grub boot menu during ubuntu's installation (important). Inshallah the problem will gone.This happened to me too.

---

### Post by deadflowr on 2014-07-09
moved to ***Other OS/Distro Support***

---

### Post by hbutt875 on 2014-07-09
go to linux mint's forum.

---

### Post by oldfred on 2014-07-09
Windows 8 is notorious at resetting itself as first in UEFI boot order as that is easy to do, but I do not think Windows 7 does that.
And HP's often are configured to only boot Windows UEFI entry and you have to use other boot keys to boot any other install whether UEFI or BIOS.

There are work arounds to get systems to boot Linux installs.
       [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
    
Shows boot order & available devices in UEFI. Must boot in UEFI mode. Secure boot only has systems installed with secure boot, but Windows 7 does not have secure boot mode, so you cannot turn it on in UEFI if available and have Windows 7 work.
 sudo efibootmgr -v

---

