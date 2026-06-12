---
title: "TestingOnMacbook Boot grub2 in EFI mode"
date: 2011-03-29
forum: Apple Hardware Users
---

### Post by metatechbe on 2011-03-29
Hello,

For some reason the page
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
is taken down, so here is the backup (in attachment)

TestingOnMacbook Boot grub2 in EFI mode

metatech

P.S. : The page is now renamed into 
[http://grub.enbug.org/TestingOnUEFI](http://grub.enbug.org/TestingOnUEFI)

P.S. : The page is now moved to 
[http://help.ubuntu.com/community/UEFIBooting](http://help.ubuntu.com/community/UEFIBooting)

---

### Post by metatechbe on 2011-03-30
Hello,

It's back on line.
It was probably an accident and not intentional.

metatech

---

### Post by the-ridikulus-rat on 2011-03-31
Please see [http://lists.gnu.org/archive/html/grub-devel/2011-03/msg00073.html](http://lists.gnu.org/archive/html/grub-devel/2011-03/msg00073.html) and subsequent replies to this thread. I guess due to lot of spam in grub.enbug.org, it may need to be moved elsewhere.

Also I am an Archlinux user and I boot grub x86_64-efi in non-Apple (Tianocore EDK2 DuetPkg UEFI 2.3). I wrote some instructions on how to set it up in archwiki at [http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2) . Any comments and suggestions about that are welcome. I guess you are more active in ubuntu forum. Also [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html) from GPT fdisk author. Regards.

---

### Post by metatechbe on 2011-04-01
> **skodabenz said:**
> Also I am an Archlinux user and I boot grub x86_64-efi in non-Apple (Tianocore EDK2 DuetPkg UEFI 2.3). I wrote some instructions on how to set it up in archwiki at [http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2) . Any comments and suggestions about that are welcome. I guess you are more active in ubuntu forum. Also [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html) from GPT fdisk author. Regards.

skodabenz,

Thanks for the information, it is also interesting to have feedback on non-Apple hardware.
On your hardware, was the kernel patch "Run EFI in physical mode" needed or not ?
Which graphic card do you have ?
Does suspend/resume work for you ?

Thanks in advance,

metatech

---

### Post by the-ridikulus-rat on 2011-04-01
> **metatechbe said:**
> skodabenz,

Thanks for the information, it is also interesting to have feedback on non-Apple hardware.
On your hardware, was the kernel patch "Run EFI in physical mode" needed or not ?
Which graphic card do you have ?
Does suspend/resume work for you ?

Thanks in advance,

metatech

Both x86_64 Vanilla Kernel (2.6.38-rc2) and x86_64 Arch's 2.6.38.1 kernel boot without any problems. I am the person who merged TestingonEFI and TestingonMacbook (changing the latter  page's title and added non-mac info) ([http://grub.enbug.org/TestingOnMacbook?action=info](http://grub.enbug.org/TestingOnMacbook?action=info) - Keshav P R).

There is no need for any patch. It works without 'noefi' option and I am getting proper framebuffer (efi_gop) support. I have ATI Mobility Radeon HD3450 (RV620 aka R600) 'radeon' module Gallium3D drivers. I have not yet tried suspend/resume though. I always shutdown and power-on the system when needed.

It iss only the Macs which have a screwed up EFI firmware. Non-Mac systems like the newer SandyBridge motherboards work perfectly with grub2 x86_64-efi , Fedora grub-legacy efi and elilo . Mine is a proper UEFI 2.3 spec x86_64 firmware from the Intel's BSD licensed Tianocore project. You might have heard of OVMF or DUET (Hackintosh XPC bootloader is based on this) firmwares. OVMF is UEFI for virtual machines. QEMU directly uses OVMF while VirtualBox adds its own patches on top of that.

My DUET firmware build (UEFI 2.3 x86_64 only) are at [http://github.com/skodabenz/](http://github.com/skodabenz/) if you want to try them. Tianocore source is at [http://tianocore.git.sourceforge.net/git/gitweb.cgi?p=tianocore/edk2;a=summary](http://tianocore.git.sourceforge.net/git/gitweb.cgi?p=tianocore/edk2;a=summary) . OVMF info at [https://sourceforge.net/apps/mediawiki/tianocore/index.php?title=OVMF_FAQ](https://sourceforge.net/apps/mediawiki/tianocore/index.php?title=OVMF_FAQ) . VirtualBox (EFI part alone) source is at [http://www.virtualbox.org/browser/trunk/src/VBox/Devices/EFI](http://www.virtualbox.org/browser/trunk/src/VBox/Devices/EFI) .

If you want help with non-Mac uefi systems, I can help you. I am not active in ubuntu forums though as i dont use it. I am active in #grub and #archlinux in freenode irc, or in grub-devel mailing list.

If you are booting Windows and want to boot it in GPT, this might be interesting to you [http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440) .

---

### Post by the-ridikulus-rat on 2011-04-01
Also the clean up of spam as well as clean up of doc has been taken up by the grub2 devs. [http://grub.enbug.org/RecentChanges](http://grub.enbug.org/RecentChanges)

---

### Post by the-ridikulus-rat on 2011-04-04
> **metatechbe said:**
> skodabenz,

On your hardware, was the kernel patch "Run EFI in physical mode" needed or not ?

metatech

That patch looks promising. It seems to work for Intel UEFI implementations too. Has it been submitted upstream. Is it a part of kernel 2.6.38 or 2.6.39 series?

---

### Post by the-ridikulus-rat on 2011-04-15
I have moved TestingOnMacbook page to [http://grub.fsij.org/TestingOnUEFI](http://grub.fsij.org/TestingOnUEFI) and its better both Mac and non-Mac (U)EFI info are added to same page.

---

### Post by Sloth on 2011-04-16
> **skodabenz said:**
> That patch looks promising. It seems to work for Intel UEFI implementations too. Has it been submitted upstream. Is it a part of kernel 2.6.38 or 2.6.39 series?

Don't see it in either one; disappointing, as I think it's needed for all newer MacBooks to boot w/o noefi.

---

### Post by volex on 2011-04-16
Here donot work~~anyone can help ?

Makbook Air 3.2(13", 2010) , EFI64, grub-efi-x86_64, Arch-x86_64 kernel, 
    1. First i use kernel 2.6.38, i have to add "noefi" to kernel boot parameters otherwise the screen turns black when i press enter in the grub menu, even though, the keyboard donot work during the whole booting process~~i canot logon ..
    2. I tried to patch "run efi in physical mode" to kernel 2.6.38, but there are several files lack in the kernel source tree(i.e. efi.c efi_64.c), i couldnot apply the patch to this version...
    3. I downloaded the 2.6.35 souce, and applied the patch, rebuilded the kernel and initrd, and it boots without add "noefi" but the kernel counld find root filesystem /dev/sda5(ext4)~~~lead me to ramfs rescue shell, but the keyboard still donot work ~~~

The wired thing is I can use keyboard editing the grub parameters but the keyboard lost reaction when the kernel boots....

    Have been scratch for several days... anyone could help ?

---

### Post by hanfi on 2011-04-17
> **volex said:**
> Here donot work~~anyone can help ?
The wired thing is I can use keyboard editing the grub parameters but the keyboard lost reaction when the kernel boots....

    Have been scratch for several days... anyone could help ?
Make sure you have Device Drivers->HID Devices->Special HID Drivers-> Apple/i{xxx}Apple enabled (HID_APPLE, prompt changed with kernel versions).

---

### Post by metatechbe on 2011-04-17
> **volex said:**
> the kernel counld find root filesystem /dev/sda5(ext4)~~~lead me to ramfs rescue shell, but the keyboard still donot work ~~~


Which version of grub are you using ?
What "-p" option do you use when building grub ?
Could you please send the error message "verbatim" (without rephrasing it) ?

Thanks.

metatech

---

### Post by volex on 2011-04-18
> **hanfi said:**
> Make sure you have Device Drivers->HID Devices->Special HID Drivers-> Apple/i{xxx}Apple enabled (HID_APPLE, prompt changed with kernel versions).

Thanks, hanfi....
I guess this is it, i was thinking if it the problem of usbinput...
I will do some scratch later...and post the results....

---

### Post by volex on 2011-04-18
> **metatechbe said:**
> Which version of grub are you using ?
What "-p" option do you use when building grub ?
Could you please send the error message "verbatim" (without rephrasing it) ?
metatech

Thanks for your reply, metatechbe,
I use grub2-1.99-efi, 
The grub2 works fine, althouth i did some scratch about the "prefix" and the root-dir...
I researched the question and read some posts, i realize that that might be the problem of SSD Driver... i will try and post results later... 
Thanks again...


+++++++++++++++++++++++++++++++++++++++++++

Solved:
To install linux to Macbook Air, 
We need some patches:
1. Run EFI in physical mode - boot direct to EFI mode
2. MBA HID - keyboard support
3. MBA ALSA - sound support

---

### Post by the-ridikulus-rat on 2011-04-21
metatechbe: I modified [http://grub.fsij.org/TestingOnUEFI](http://grub.fsij.org/TestingOnUEFI) extensively adding some non-mac uefi specific info. Check whether mac info are correct.

---

### Post by metatechbe on 2011-05-03
Grub Wiki has been down for a week now&#8230;
The backup of the TestingOnUEFI page is in attachment on the first post of this thread :
[http://ubuntuforums.org/showpost.php?p=10615203&postcount=1](http://ubuntuforums.org/showpost.php?p=10615203&postcount=1)

Regards,

metatech

---

### Post by metatechbe on 2011-05-03
From this post I understand that the Grub wiki has been decommissioned :
[http://lists.gnu.org/archive/html/grub-devel/2011-03/msg00122.html](http://lists.gnu.org/archive/html/grub-devel/2011-03/msg00122.html)

We need another Wiki to move into.
Maybe this one ?
[http://help.ubuntu.com/community/UEFIBooting](http://help.ubuntu.com/community/UEFIBooting)

Regards,

metatech

---

### Post by metatechbe on 2011-05-08
Hello,

The page is now hosted on 
[http://help.ubuntu.com/community/UEFIBooting](http://help.ubuntu.com/community/UEFIBooting)

Regards,

metatech

P.S. The page was renamed to UEFIBooting to unify Mac and PC instructions

---

