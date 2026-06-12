---
title: "Boot-repair needs repository for a grub-efi package? Fedora"
date: 2013-02-15
forum: Any Other OS
---

### Post by eagles8804 on 2013-02-15
So I am using Ubuntu Secure Remix to attempt to repair my broken system (not really BROKEN, but after installing Fedora 17, I can't boot into Windows 8).

Here is the summary that the tool gave me to report back to this forum.
[http://paste.ubuntu.com/1661337/](http://paste.ubuntu.com/1661337/)

When I run boot-repair, I get either a RAID message warning or I am told "Please enable a repository containing the [grub-efi] packages in the software sources of Linux (mapper/vg_bigpapa-lv_root). Then try again."

I do not use RAID, but an LVM if that helps. And yes, bigpapa is my computer's name.

---

### Post by oldfred on 2013-02-16
Moved to other OS since Fedora.

Do not know if Fedora works with secure boot or not. Be sure to have secure boot off and fast boot off in Windows.

It looks like Boot-Repair is trying to install grub-efi with Fedora, but cannot find it.

I do know that with BIOS installs, you have to from Ubuntu install the lvm2 driver and mount the Fedora partition to get the os-prober to find the Fedora install. Since lmv is intended to allow flexibility on partitions and in multiple boot systems that is not required unless entire drive is lvm, many just change to ext4 partition not lvm to install Fedora.

You have Window in UEFI, so you need  Fedora in UEFI mode. 

If you can boot Fedora just install grub-efi and uninstall grub-pc. In Fedora does grub-efi have a slightly different package name?
> grub-efi NOT available (yum info name  problem)        Multiple installs - Ubuntu, Fedora, Arch based Manjaro, Mint 14
[http://ubuntuforums.org/showthread.php?t=2086602](http://ubuntuforums.org/showthread.php?t=2086602)
[http://paste.ubuntu.com/1382319/](http://paste.ubuntu.com/1382319/)

---

