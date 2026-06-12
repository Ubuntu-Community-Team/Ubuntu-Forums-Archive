---
title: "Macbook with bad cd drive, grub2 hangin"
date: 2010-06-14
forum: Apple Hardware Users
---

### Post by Hospadar on 2010-06-14
I have a macbook pro 4,1 which does not have a functioning cd drive.  I'm trying to install ubuntu by loop-booting an iso from the hard drive (or a usb drive, or using the netbook kernel, or the files from a live usb, or anything really)

It will not boot off of usb drives.  I've read that this is an issue with the firmware of these machines and there's not much I can do about it.  rEFIt sees the usb drive, but the macbook complains there is no OS when it attempts to boot from it.

I've installed grub2 locally by dropping a home-built grub.efi (And modules and whatnot) in /efi/grub.  This lets me pick grub from the refit menu, and grub will correctly load up a grub.cfg, and I can get into a grub shell and browse around, pick kernels etc.

The problem comes when I try to boot anything.  I've tried the netboot kernel and initrd, I've tried loop booting an ISO, I've tried copying a live usb to disk and booting that kernel, but no dice.  any way I go about it, I can select the kernel and initrd, and that appears to work fine.  Grub gives me some correct-looking info messages about the kernel and initrd that I just loaded, but then when I try to actually boot (i.e. with the boot command), nothing happens, I just get a cursor that sits there and does nothing.

I've tried with everything (the iso, the kernel and initrd) on the first partition, on other partitions, with different filesystems (both hfs+ and fat32) all to no avail, and all with the same symptoms, grub just sits there after the kernel and initrd are loaded and does nothing.

I'm wondering if there's some kernel arguments I need to make things happen on the macbook or some other magic like that.  This is a pretty non-ordinary boot setup so it's not terribly easy to find info about it.

Any help would be greatly appreciated

These are some relevant links:
[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
[http://ubuntuforums.org/showthread.php?t=1224417&page=5](http://ubuntuforums.org/showthread.php?t=1224417&page=5) (post #48 seems to be the same problem)

---

### Post by linuxopjemac on 2010-06-14
Can't you do a netinstall?
[ftp://ftp.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso](ftp://ftp.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso)

It will install Lucid over the net.

---

### Post by Hospadar on 2010-06-14
No can do, the netinstall still needs to boot a linux kernel at some point, and I can't make that happen.  I've tried the netinstall kernel already with no luck.

---

