---
title: "asus q500a: windows8/ubuntu12.04 dual boot"
date: 2013-08-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by seth4 on 2013-08-25
I have seen a few posts where people are having trouble accomplishing this. I struggled for a couple weeks with it, and now have it working fine. Still having some trouble with my hardware in ubuntu (see my other post) but the dual boot is working.
-First I tapped delete while rebooting to get to bios. Disabled secure boot, enabled launch csm and launch pxe oP ROM. I honestly don't know what these are, or if it was necessary to do so, but disabling secure boot is important. Once secure boot was disabled, I put in my flash disk with ubuntu 12.04 desktop formatted as fat, and successfully booted live (tap f12 to get to temp device menu). Pretty much everything worked great from live, including touchscreen! So I installed ubuntu on it's own partition (ext4) and set it as root/primary partition. 
-Now in my start devices I have a windows bootloader and a ubuntu bootloader. Although grub recognized the windows 8 bootloader, it did not successfully boot it. Vice versa for windows. (DONT DO THIS) From this point I booted to ubuntu, installed grub 2, and did "sudo update-grub". THIS FAILED. It prevented either operating system from booting.
-After trying a boot-repair cd and having no success I booted to ubuntu live again and installed the boot-repair utility from software center. I ran that and just went with the default settings. Now grub give me a windows uefi.efi or something like that, and it successfully boots windows and ubuntu from the same bootloader. SUCCESS!
It would seem to me that after disabling secure boot and installing ubuntu, if you were to simply boot to ubuntu and run the boot-repair utility from there it should work just fine. I included all the steps that I took, even the ones that didn't work. I do not recommend doing everything I have mentioned.

---

### Post by oldfred on 2013-08-25
Best not to turn on CSM as that is the BIOS mode and Ubuntu needs to be installed in UEFI mode to dual boot with Windows. But a few systems will not let you install in UEFI mode.
Also a few systems will only boot Windows in secure boot mode. For those you have to leave secure boot on and install Ubuntu in secure boot mode. 

Grub does have a year old unresolved bug on creating UEFI boot entries for Windows. It still creates BIOS type entries that do not work with UEFI. Boot-Repair fixes that.

---

### Post by seth4 on 2013-08-25
How do you install Ubuntu in UEFI mode? I don't think I did that.

---

### Post by oldfred on 2013-08-25
It is how you boot. From UEFI menu with UEFI turned on and CSM off, then you should get the choice to boot in UEFI mode.
DVD or flash drive is configured to boot in either UEFI or BIOS and how you boot is how its installs.
If you get grub menu then you are booting with UEFI.
If you get accessibility screen with little icons at bottom that is BIOS.

---

### Post by seth4 on 2013-08-26
I do have CSM enabled, and I did before I installed ubuntu. I suppose uefi just overrides csm?

---

### Post by oldfred on 2013-08-26
No, most systems will just boot with CSM if you have it on, and do not know about UEFI.

A few only have two settings, UEFI with secure boot and CSM where CSM tries UEFI (without secure boot) and if that fails then try MBR for a boot loader.

But if you installed Ubuntu in CSM mode Boot-Repair can convert it to UEFI by uninstalling grub-pc and installing grub-efi.

---

### Post by seth4 on 2013-08-29
Okay, the Ubuntu 12.04 Desktop live works without launch CSM enabled as well. For some reason every time I unplug the usb the boot order reverts back so I have to tap delete and change the order each time I use it.

---

### Post by oldfred on 2013-08-29
You can tell if booting in BIOS/CSM mode as you get purple screen and tiny accessibility icons at bottom of screen. If booting in UEFI mode you get standard grub menu.

You should also have a one time boot key that lets you boot flash drive without changing boot order  in UEFI/BIOS.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by seth4 on 2013-08-31
Yeah, I found a temporary boot device menu. It is esc.

---

