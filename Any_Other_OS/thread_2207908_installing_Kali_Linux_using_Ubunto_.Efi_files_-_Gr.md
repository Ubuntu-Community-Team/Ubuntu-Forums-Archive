---
title: "installing Kali Linux using Ubunto .Efi files - Grub.cfg help needed!"
date: 2014-02-25
forum: Any Other OS
---

### Post by J.Sickness on 2014-02-25
I'm trying to install Kali Linux on my personal Windows 8 laptop (Sony Vaio Flip 15).


To my knowledge there are currently only two distributions of Linux that support Windows 8 (Ubuntu and Fedora)
I have tried Ubuntu with no errors running the distro live.(I did not try installing it)
However, for the tasks I'm trying to accomplish I need Back track5 r3 (or *preferably) Kali

I have currently installed Kali Linux on a USB flash drive using: Universal USB Installer

At this point, I have configured my laptop to boot from an external device before booting form the internal hard drive. I understand Windows 8 uses Unified Extensible Firmware Interface (UEFI) and not BIOS. Therefore, I have disabled secure boot and created the following directory in my USB flash drive root.

/EFI/BOOT
Within this directory I have copied (Bootx64.efi & Grubx64.efi) from Ubuntu; additionally, I have created a Grub.cfg file which I have pasted at the bottom of this post.

As of now I have been able to
1). Boot into GRUB shell - Unfortunately I do not know how to boot Kali from the shell
When I attempt command boot (error: you need to load the kernel first)
2). Boot kali install menu - when I attempt to run the distribution live it encounters the following errors:
Error: Disk 'hd0,1' not found
Error: You need to load the kernel first


In an attempt to fix the above 'hd0'1' error I have changed the set root=(hd0,1) to (hd1,1) as my USB is currently listed as disk 1 (under windows management)

After changing the hd, the grub recognizes the HD but can not find:
/live/vmlinuz boot=live noconfig=sudo username=root hostname=kali
*VMLINUZ is the file It needs to find*

So basically (I'm assuming) I'm still not booting the correct hd? because the usb contains the live folder and has vmlinuz file in it!


IS THERE ANY WAY TO ENSURE THE CORRECT (hd0,1) or (hd1,1) or (hd?,?)
Also, what's with grub saying I need to boot the kernel first ?
(am I not already trying to do that?)







Grub.cfg


# Config file for GRUB2 - The GNU GRand Unified Bootloader
# /boot/grub/grub.cfg

# DEVICE NAME CONVERSIONS
#
# Linux Grub
# -------------------------
# /dev/fd0 (fd0)
# /dev/sda (hd0)
# /dev/sdb2 (hd1,2)
# /dev/sda3 (hd0,3)
#
# root=UUID=dc08e5b0-e704-4573-b3f2-cfe41b... persistent

set menu_color_normal=yellow/blue
set menu_color_highlight=blue/yellow

function load_video {insmod efi_gop
insmod efi_uga
insmod video_bochs
insmod video_cirrus
insmod all_video}

load_video
set gfxpayload=keep

# Timeout for menu
set timeout=5

# Set default boot entry as Entry 0
set default=0
set color_normal=yellow/blue

menuentry "Kali - Boot Non Persistent Mode" {set root=(hd0,1)
linuxefi /live/vmlinuz boot=live noconfig=sudo username=root hostname=kali
initrdefi /live/initrd.img}

menuentry "Kali - Boot Persistent" {set root=(hd0,1)
linuxefi /live/vmlinuz boot=live noconfig=sudo username=root hostname=kali persistence
initrdefi /live/initrd.img}

menuentry "Kali Failsafe" {set root=(hd0,1)
linuxefi /live/vmlinuz boot=live config memtest noapic noapm nodma nomce nolapic nomodeset nosmp nosplash vga=normal
initrdefi /live/initrd.img}

menuentry "Kali Forensics - No Drive or Swap Mount" {set root=(hd0,1)
linuxefi /live/vmlinuz boot=live noconfig=sudo username=root hostname=kali noswap noautomount
initrdefi /live/initrd.img}

menuentry "Kali Graphical Install" {set root=(hd0,1)
linuxefi /install/gtk/vmlinuz video=vesa:ywrap,mtrr vga=788 initrdefi /install/gtk/initrd.gz}

menuentry "Kali Text Install" {
set root=(hd0,1)
linuxefi /install/vmlinuz video=vesa:ywrap,mtrr vga=788
initrdefi /install/initrd.gz}

---

### Post by QIII on 2014-02-25
[I]Moved to [B]Other OS/Distro Support

[/B][/I]Might I suggest the [Kali Forums]("http://forums.kali.org/") as a better place to address this?

---

