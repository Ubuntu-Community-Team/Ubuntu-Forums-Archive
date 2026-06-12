---
title: "debian alongside windows8"
date: 2012-12-13
forum: Any Other OS
---

### Post by warheart2 on 2012-12-13
yesterday i installed debian wheezy alongside with windows 8, but for some reason grub is not showing an option for windows.
i tried 
root@debian:~# grub-install /dev/sda Installation finished. No error reported.
then restarted but didn't work.

on gparted i saw that debian is on dev/sda6, is mounted on the /,
and is bootable.
windows is on dev/sda4 the file system is unknown, not mounted, and has flags
of bios-grub
what can i try?

---

### Post by sdowney717 on 2012-12-13
Try this

[http://www.supergrubdisk.org/wiki/SuperGRUB2Disk](http://www.supergrubdisk.org/wiki/SuperGRUB2Disk)

---

### Post by warheart2 on 2012-12-13
yeah I tried supergrub but it didn't work

---

### Post by lisati on 2012-12-14
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by coffeecat on 2012-12-14
If your machine came with Windows 8 pre-installed it is almost certainly a UEFI system with a GUID partition table. With Ubuntu you need to boot the Ubuntu install CD in EFI mode in order that the EFI version of grub is used. This Ubuntu community documentation page is primarily about installing Ubuntu in EFI mode but it gives some useful information about UEFI/GPT:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I don't know about the specifics of Debian with UEFI, but this Debian forum thread may give you some pointers:

[http://forums.debian.net/viewtopic.php?f=16&t=81120](http://forums.debian.net/viewtopic.php?f=16&t=81120)

---

### Post by kiyop on 2012-12-14
A partition with bios_grub flag may not be windows system partition.
It may be BIOS BOOT PARTITION.
I wonder if you deleted the windows system partition, judging from the fact that Super Grub2 disk could not solve your problem. (Of course, it is possible that you did wrong thing with Super Grub2 disk.)
 
If you can, execute the following on debian with root privilege and post the result.
```
blkid | sed -e "s/ UUID=\"[^\"]*\"//"
```If there is Windows partitions, execute on debian with root privilege,
```
update-grub
```You can execute boot info script to analyze the current situation of boot.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Although I may be wrong, EFI version of Grub2 maybe does not need BIOS BOOT PARTITION.
Ordinary grub2 (non-EFI version) needs BIOS BOOT PARTITION for HDD with GPT.
If UEFI is used, EFI SYSTEM PARTITION maybe is used.
I wonder if your PC had used UEFI before you installed debian.
I wonder if your installation of debian messed up the boot configuration.

---

### Post by oldfred on 2012-12-14
Several users have installed Ubuntu in BIOS mode on UEFI systems. But Boot-Repair will convert them to UEFI boot by uninstalling grub-pc and installing grub-efi.

Not sure if it directly works with Debian.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by warheart2 on 2012-12-14
i ran blkid | sed -e "s/ UUID=\"[^\"]*\"//"

```
blkid | sed -e "s/ UUID=\"[^\"]*\"//"
/dev/sda1: LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: LABEL="ESP" TYPE="vfat" 
/dev/sda5: LABEL="Push Button Reset" TYPE="ntfs" 
/dev/sda6: TYPE="ext4"
```

---

### Post by kiyop on 2012-12-14
> **warheart2 said:**
> i ran blkid | sed -e "s/ UUID=\"[^\"]*\"//"

```
blkid | sed -e "s/ UUID=\"[^\"]*\"//"
/dev/sda1: LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: LABEL="ESP" TYPE="vfat" 
/dev/sda5: LABEL="Push Button Reset" TYPE="ntfs" 
/dev/sda6: TYPE="ext4"
```
Thanks for your reporting the result :)

I do not know well about Windows 8, but judging from the LABEL and the filesystem of the reported partitions...
/dev/sda1 seems to be a partition for recovery.
/dev/sda2 seems to be an EFI SYSTEM partition.
/dev/sda6 seems to be the debian / partition.

I am not sure whether /dev/sda5 is the windows system partition or not. I am not familiar with its label "Push Button Reset".

I suggest you executing boot info script or boot repair, which was suggested by oldfred.

I am curious about the current situation of your PC.
You can know the partition table of the HDD by
```
fdisk -l
apt-get update
apt-get install gdisk parted
parted -l
gdisk -l /dev/sda
```You can list the contents of /dev/sda5 by
```
mount -t ntfs-3g /dev/sda5 /mnt -o ro
ls /mnt -l
umount -l /mnt
```

---

### Post by warheart2 on 2012-12-14
windows 8 is installed on /dev/sda4 but the file system is unknown for g parted, I don't know if windows 8 has an NTFS file system, i'll try that boot repair

---

### Post by kiyop on 2012-12-14
> **warheart2 said:**
> windows 8 is installed on /dev/sda4 but the file system is unknown for g parted, I don't know if windows 8 has an NTFS file system, i'll try that boot repair
For Windows 8 server, a newer filesystem REFS may be supported, although I am not sure.
[http://superuser.com/questions/496540/is-windows-8-able-to-read-partitions-formatted-with-the-refs-filesystem](http://superuser.com/questions/496540/is-windows-8-able-to-read-partitions-formatted-with-the-refs-filesystem)

---

### Post by UltimateCat on 2012-12-15
I have been studying this topic for weeks.

You have to disable the secure boot.

Extract the OS Vendors key exchange key from it and install it to the database-

For Linux to access UEFI Runtime Services the UEFI firmware processor architecture and the Linux kernel processor must match. It is independent of the bootloader used.  Otherwise you will have Kernel Panic.  It's advised to use Kernel 3.0 or above.

I have learned from other Linux forums 2 things:
You have to set the BIOS in BIOS mode then do the install via standard PXE; your machine will be in BIOS mode.

With Secure Boot disabled you have cd boot. No GPT boot so the disk won't boot. Just MBR and CD boot with Secure boot disabled.

[http://fedoraproject.org/wiki/Features/EFI](http://fedoraproject.org/wiki/Features/EFI)
[http://www.linuxfoundation.org/search/node/pdf%20uefi]("http://www.linuxfoundation.org/search/node/pdf%20uefi")

[http://www.pcworld.com/article/259801/fedora_linux_moves_forward_with_uefi_secure_boot_plans.html](http://www.pcworld.com/article/259801/fedora_linux_moves_forward_with_uefi_secure_boot_plans.html)

---

### Post by oldfred on 2012-12-15
UltimateCat's suggestions will convert you back to BIOS mode, but you will not be able to use Windows 8 from your pre-installed system. If you have another full install of Windows 8, it should install in MBR mode.

Windows only boots from gpt drives with UEFI. 

Ubuntu will boot either BIOS or UEFI from gpt partitioning or BIOS from MBR(msdos) partitioning. 

Most Linux boot UEFI, the new issue is secure boot which all new systems with Windows 8 have. Ubuntu is one of the first to install with secure boot on. Debian may not even work with secure boot. If it worked with older UEFI systems it should work with secure boot off. 

But we are finding that some systems work, some only work with secure boot off and some do not seem to work. May be UEFI bugs or settings that users have not learned to change (and we do not know to suggest as it is so new).

UEFI bug:
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

    
But we have other Lenovo's that have worked.

       [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

---

### Post by kiyop on 2012-12-15
> **oldfred said:**
> (snip by kiyop)

Ubuntu will boot either BIOS or UEFI from gpt partitioning or BIOS from MBR(msdos) partitioning. 

Most Linux boot UEFI, the new issue is secure boot which all new systems with Windows 8 have. Ubuntu is one of the first to install with secure boot on. Debian may not even work with secure boot. If it worked with older UEFI systems it should work with secure boot off. 

But we are finding that some systems work, some only work with secure boot off and some do not seem to work. May be UEFI bugs or settings that users have not learned to change (and we do not know to suggest as it is so new).

(snip by kiyop)
Thanks oldfred to notice the above.
I found:
[http://www.debian.org/devel/debian-installer/News/2012/20121018.en](http://www.debian.org/devel/debian-installer/News/2012/20121018.en)
> Debian Installer 7.0 Beta3 release
October 18th, 2012

(snip by kiyop)

Add EFI support for 64-bit PCs (amd64), allowing installation   in EFI mode instead of using the legacy BIOS. This does **not** include   any support for UEFI Secure Boot — that will come later.
I will dig in booting with secure boot.

---

### Post by YannBuntu on 2012-12-16
Hello

Boot-Repair will fix Debian's boot the same way it does for Ubuntu.
Here are the steps to follow: [http://ubuntuforums.org/showpost.php?p=12406192&postcount=687](http://ubuntuforums.org/showpost.php?p=12406192&postcount=687)

Remarks:
- Debian can't boot in SecureBoot at all, because it has no signed packages.
- depending on the Debian's version, Debian's grub-efi packages may be older, so may have more bugs. See [http://packages.debian.org/search?keywords=grub-efi](http://packages.debian.org/search?keywords=grub-efi) and [http://packages.ubuntu.com/search?grub-efi](http://packages.ubuntu.com/search?grub-efi)

---

