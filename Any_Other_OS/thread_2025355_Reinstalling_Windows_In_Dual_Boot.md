---
title: "Reinstalling Windows In Dual Boot"
date: 2012-07-14
forum: Any Other OS
---

### Post by manco on 2012-07-14
Hey everyone, my apologies if this is posted in the wrong place.

I recently worked on a friend's computer installing Xubuntu 12.04 and Windows XP.

Xubuntu is working great, but I need to reinstall Windows XP.

I know this is kind of a Windows XP question, but if I simply delete the Windows XP partition and reinstall XP over it, will everything work the way it was?

Thanks!

---

### Post by Cheesemill on 2012-07-14
XP will overwrite the boot loader. It's a simple fix though, you just need to run boot-repair from a Live CD after you've installed Windows.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-07-14
Moved to Other OS.

Yes, but Windows will overwrite the MBR and only boot Windows. You need your Ubuntu liveCD or USB or other repair ISO to reinstall grub2's boot loader and then a new sudo update-grub. (sometimes old Windows entry even works.)

The requirement for Windows to install is a primary NTFS formated partition with the boot flag. IF Windows was working before then your existing NTFS partition should be a primary and have the boot flag.

If you want a gui to reinstall.
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Or the short version is just a couple of commands from liveCD terminal.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by manco on 2012-07-14
> **oldfred said:**
> Moved to Other OS.

Yes, but Windows will overwrite the MBR and only boot Windows. You need your Ubuntu liveCD or USB or other repair ISO to reinstall grub2's boot loader and then a new sudo update-grub. (sometimes old Windows entry even works.)

The requirement for Windows to install is a primary NTFS formated partition with the boot flag. IF Windows was working before then your existing NTFS partition should be a primary and have the boot flag.

If you want a gui to reinstall.
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Or the short version is just a couple of commands from liveCD terminal.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Thanks! :D

I'm going to look into "Boot Repair". Once I have the computer again to work on I'll give it a shot :)

---

