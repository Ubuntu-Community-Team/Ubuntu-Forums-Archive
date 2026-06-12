---
title: "Need help Installing Ubuntu dualboot on laptop"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by madmesh on 2007-02-21
I need some help installing Ubuntu 6.10 on my laptop. I already have a Windows XP installation on the laptop but I want to add Ubuntu as wel. Most of the installation process goes well untill the partitioning, Ubuntu doesn't seem to recognize my harddrive.

My harddrive is 120 GB with one NTFS partition for Windows XP (30 GB) which is already installed, the rest is still "unpartitioned space". I need one FAT32 partition of at least 30 GB (I havent partitioned that yet) to exchange data between Linux and Windows. The rest is reserved voor Ubuntu.

I'm a Linux beginner, I have installed Fedora Core 3 once on my desktop system but thats it.

My system:
Dell Inspiron 1501 laptop

Can anyone give me some advice?

---

### Post by Bachstelze on 2007-02-21
You won't need to do anything special since you already have free space, just install Ubuntu there and you will be fine.

Oh and also, you can go without a FAT partitions, there are very good ext2/3 drivers for Windows out there :)

---

### Post by madmesh on 2007-02-21
I dont think my hard disk is recognized by the installer so I dont get any options to specify the partions Linux needs.

I only get the option "manually edit partition table", and I cant uncheck that option. When I press "forward" the installer starts searching for hardware and tells me that the device is not ready or not found. After that I get a screen with a pulldown menu for the partitions Linux needs like: /home /boot

But I cant assign disk space to those partitions and format them, so I cant install Ubuntu.

---

### Post by madmesh on 2007-02-21
*bump*

---

### Post by chiujason on 2007-02-21
This site helps with our laptops:
[http://ubuntu1501.blogspot.com](http://ubuntu1501.blogspot.com)

---

### Post by madmesh on 2007-02-22
That site was really helpfull, but not quite enough i'm afraid.

Apparently I need to do the following:
**Sudo gedit /boot/grub/menu.lst**

This wil edit grub to recognize my SATA hard disk. Unfortunately I dont know how to reach it because I'm booting from a DVD so my fstab is empty. None of my newly formatted disks apear there and the entire filesystem is actually the one on my DVD not the one I just installed. When I enter the above command in a terminal I think I am actually creating the menu.lst file instead of editing an existing one since it comes up empty. When I look in the /boot folder there isnt even an grub subdirectory.

To permenantly change the hd detection I need to alter the following from:
**kernel  /boot/vmlinux-2.16.17.10-generic root=/dev/sda1 ro quiet splash**
to:
**kernel  /boot/vmlinux-2.16.17.10-generic root=/dev/sda1 ro quiet splash pci=nomsi**
By adding **pci=nomsi** at the end.

Is there any way to edit this file by booting from the DVD?

---

