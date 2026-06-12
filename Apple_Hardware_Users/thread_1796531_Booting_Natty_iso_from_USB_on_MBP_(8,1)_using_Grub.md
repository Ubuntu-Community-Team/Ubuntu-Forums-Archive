---
title: "Booting Natty iso from USB on MBP (8,1) using Grub2"
date: 2011-07-03
forum: Apple Hardware Users
---

### Post by OSXBen on 2011-07-03
After two days, I finally have refit, Grub2 w/ EFI support booting Ubuntu 64 bit's kernel from a USB flash drive on a MBP(8,1), however it does not seem to be able to find the iso file to boot from. Here's my grub.cfg
```
menuentry "Ubuntu Live 11.04 64 bit" {
insmod efi_gop
set iso=/ubuntu-11.04-desktop-amd64.iso
loopback loop $iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$iso noeject noprompt noefi --
initrd (loop)/casper/initrd.lz
}
```The error after the kernel loads is: 
```
/scripts/casper-premount/20iso_scan: line 46: can't open /dev/sr0: No medium found

Could not find the ISO /ubuntu-11.04-desktop-amd64.iso
<cut>
(initramfs)
```At this point the keyboard is non-functional at the initramfs prompt

Hoping that someone has some sage advice. I can get it to boot if I dump the squashfs filesystem on the flash drive or had a natty disc in the system, but that will not work for my needs.

---

### Post by oldfred on 2011-07-04
I do not know if it works with efi boots.

This is my stanza that I used to install from. I think you need to add quotes on set isofile line. I have to have nomodeset to boot with my nVidia card.

```
menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/ubuntu-11.04-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by OSXBen on 2011-07-04
> **oldfred said:**
> I think you need to add quotes on set isofile  line. I have to have nomodeset to boot with my nVidia card.

I gave it a shot with quotes and the nomodeset kernel parameter, but that did not seem to change my circumstances. Also tested on Macbook(5,2).

Can you tell me which version of grub you are using and if it is stock  or compiled with extra options ? Did you prep your USB drive in any  particular way, as particularly related to options with grub-install and  grub-mkimage ?

My USB flash drive is a [hybrid GPT/MBR disk]("http://www.rodsbooks.com/gdisk/hybrid.html") with 2 GPT partitions (MSDOS  and HFS+) and 3 MBR partitions (FAT32, HFS+ and GPT). On the HFS+  parition, I have [rEFIt]("http://refit.sourceforge.net/") enabled and GRUB compiled with EFI support and all modules installed in the FAT32 partition table and filesystem. I would be interested in your partition and filesystem layout not using the EFI mode of GRUB.

---

### Post by oldfred on 2011-07-04
The main 4GB flash I use for booting ISO with grub is just formated to FAT with one partition. Standard grub2 install. I manually created a grub.cfg in all cases.

I also installed windows repair cd to a 2GB flash but it only use about 250MB, so I installed grub2,added a windows boot stanza in grub.cfg to boot windows repair and added a second partition to also boot a few other repair ISOs. It is Fat32 & ext2.

My third flash is a 16GB full install of Ubuntu with gpt. I have three Linux partitions. The bios_grub, main install, and a data partition. Note sure now if ext2 or ext4 with journel turned off.

Boot script reports all as Grub2 (v1.97-1.98), as I installed grub2 from several versions ago.

I think I just installed grub2 to the flash drive per the link to Herman's site. Or maybe one of the other links? I reviewed all of them and did whatever seemed to work.

---

### Post by metatechbe on 2011-07-04
> **oldfred said:**
> 
Grub2 (v1.97-1.98), as I installed grub2 from several versions ago.



Grub2 v1.99 is absolutely required for UEFI booting (with the "newreloc" feature), or you risk memory corruptions because of memory overwriting.
Please see
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by drs305 on 2011-07-04
Is the ISO file in your / directory (or more precisely the root of the partition)? That is where it is looking for it since neither your "set isofile" and "iso-scan/filename" contain a folder/directory. It can be in that location, but normally we see the ISO files stored somewhere else...

---

### Post by oldfred on 2011-07-04
I am booting with BIOS not UEFI, but some of my drives, flash drives are gpt as I wanted to learn more about gpt. I now plan to convert all drives to gpt except my Windows XP drive until I totally give up on XP. 

I do have to add drive partition settings like booting an ISO on a hard drive which drs305 explains very well in this thread.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by OSXBen on 2011-07-04
> **drs305 said:**
> Is the ISO file in your / directory (or more precisely the root of the partition ?

I have done it both ways, iso nested in a directory and in the root of the filesystem. I have opted to keep it in the root of the filesystem for my troubleshooting purposes.

I am going to try a regular grub2 install and see if that works.

---

### Post by pindar on 2011-07-08
Not sure if this helps, but: I was able to make a USB key which would boot from some ubuntu/mint isos - but only version 10.10. I've never been able to boot from a natty iso. It was on the same usb key, I used exactly the same commands which worked for 10.10, but no joy. So there may be a subtle change in the way they produce the isos.

---

