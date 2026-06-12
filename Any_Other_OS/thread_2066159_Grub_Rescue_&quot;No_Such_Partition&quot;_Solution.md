---
title: "Grub Rescue &quot;No Such Partition&quot; Solution without Windows XP CD"
date: 2012-10-03
forum: Any Other OS
---

### Post by MyVitalRemains on 2012-10-03
***_[SIZE="2"]NOTE THAT THIS METHOD IS ONLY RECOMMENDED FOR PEOPLE WHO DON'T HAVE A WINXP CD AND HAVE NO EXTRA CDS TO USE FOR BOOTING UTILITIES LIKE ULTIMATE BOOT CD OR SUPER GRUB DISK.[/SIZE]   _***

If you, like me, found yourself trying to uninstall [SIZE="1"][insert GNU/Linux distro here][/SIZE] by deleting a partition and you rebooted without restoring MBR on Windows XP, then you are probably familiar with the Grub Rescue screen that looks like the following: [IMG]http://i.imgur.com/izQv7.png[/IMG] 
You may think that it is the end of your whole life on Windows XP. Well, it is not. Hopefully, you have a LiveCD available, because in order to fix this then you'll need one. 

Use a LiveCD/USB to boot into an operating system (preferably Ubuntu) and Install the OS.You may think of this as counter-productive, but it will end up being useful later on. The reason why you can't access Windows is because you don't have a bootloader to boot the OS with. Installing  it will enable you to use the GRUB bootloader. After installing it, reboot  and boot Windows XP and delete the partition you used again. Except this time use MBRWizard or MBRFix (for advanced users) to restore the Master Boot Record. 

After doing this, you should be able to boot into Windows. If not, try looking elsewhere for some other information on your specific issue. 

:popcorn:

---

### Post by oldfred on 2012-10-03
Moved to Other OS.

While I like to promote installing Ubuntu, you do not have to. Just use liveCD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Or if you like a gui:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Or you can directly instlall lilo as just a Windows like boot loader:

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

This boots many systems if found:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

