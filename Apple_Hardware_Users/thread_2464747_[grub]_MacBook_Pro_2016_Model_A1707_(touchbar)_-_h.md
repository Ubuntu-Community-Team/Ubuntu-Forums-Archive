---
title: "[grub] MacBook Pro 2016 Model A1707 (touchbar) - how to restore dual boot to windows"
date: 2021-07-11
forum: Apple Hardware Users
---

### Post by technomancer75 on 2021-07-11
Hi.

I was trying out an Ubuntu Studio Live USB (Version 20.04.2 LTS Focal Fossa) on my MacBook Pro, which was configured for Bootcamp dual boot to Windows 10.

I ended up trying to install Ubuntu Studio onto another USB stick, which succeeded, but it also installed the grub boot loader on the boot partition.

Meaning, I can still boot to MacOS, but if I select the "Windows" partition, it just starts the grub boot loader, trying to load the Ubuntu install from the USB stick.

I tried to run the Boot Repair as outlined here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But that didn't seem to change anything.

Here the Pastebin upload from the boot repair utility: [https://paste.ubuntu.com/p/PX3nMdyCvW/](https://paste.ubuntu.com/p/PX3nMdyCvW/)

How can I either remove grub and restore UEFI booting to the Bootcamp partition, or add a grub config line to do the same?

Thanks in advance for helping me out.

---

### Post by technomancer75 on 2021-07-11
I was able to dual boot into Windows again via the following grub.cfg:

menuentry "Windows 10" {
    insmod part_gpt
    insmod ntldr
    insmod ntfs
    insmod chain
    set root='(hd0,gpt1)'
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

I get a warning message about a file missing (ntldr.mod?), but after hitting Enter it continues on and starts Windows.

---

