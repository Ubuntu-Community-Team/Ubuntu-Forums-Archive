---
title: "Installing Multiple Ubuntus (or other Linux Distros) on one PC"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Jose Catre-Vandis on 2006-03-31
Hi

Am looking to install multiple Linux distros on one PC and need some help with the partitions required and settings in install

I understand I can only have one distro "booting" from the mbr, whilst any others should have their grub in their own boot partition. Correct?

Does this "boot" partition have to be created prior to installation as a seperate partition?

If during installation in partitioning, is the boot partition created automatically if I choose "/boot" as opposed to /   ? Or do I have to create a boot/root parition separately?

How do I then pick up the secondary/tertiary installations with the first grub ?

I already have XP on partition 1 (hda0), a single hard disk, and Ubuntu Dapper flight 5 on a logical partition (hda7). Plenty of unallocated space can be created in the other logical partitions between these two. Dapper seems to work fine on this logical partition, as opposed to being a single primary partition.

All help much appreciated

Jose

---

### Post by muep on 2006-03-31
Hi.

There is only one MBR in a hard disk. Ubuntu installs Grub there, which can boot Windows and multiple Linux distributions without any problem. If you install another distribution, it probably asks if you want to install Grub. 

Your existing Grub can boot the new distro, but you need to configure the old Grub to boot the new distribution. The config file will then be in the old distro. You can also install Grub with the new distribution, which sould detect all your existing operating systems and add correct boot options for them. Now the config is in the new distro.

---

### Post by aysiu on 2006-03-31
You will need a partition for each distro.
You will need one distro's Grub to be installed to the MBR (Master Boot Record).
There's no need to have a separate /boot partition, though.

---

### Post by johnnymac on 2006-03-31
You know...you can also try virtualizing the installations.  If you use Xen you can run in one and virtualize the others at almost normal performance.  Check out their site...I use it and love it.

[http://www.cl.cam.ac.uk/Research/SRG/netos/xen/](http://www.cl.cam.ac.uk/Research/SRG/netos/xen/)

---

### Post by Jose Catre-Vandis on 2006-04-02
OK here is my solution, which isn't perfect, but it worked.

The aim was to have a working installation of XP along with 5 linux distros. With Xp and Ubuntu on  baord already, a secondary aim was to maintain the existing grub boot loader for Ubuntu, and to edit it to allow the booting of the other distros. To be clear, Grub is the main bootloader for my machine occupying the mbr.

I used Acronis Director Suite on a boot cd to setup the partitions, all logical, in the extended partiton on my big hard disk. Created 4 additional partitions of 10gb, in addition to the 10 gb partition ubuntu is on and a 1gb swap partition at the end of the drive. (This is all in addition to XP on the first partition, and a couple of partitions I have for music and other stuff. I labelled each partition as I created it to help me identify them later, e.g. Ubuntu, Suse, PCLinuxOS etc.

Identify which partition Ubuntu is installed on, in my case hda7 (hd8 in Grub, grub labels partitions one number after linux)

all the empty partitions came after Ubuntu, so:
Ubuntu        hda7/hd8
Suse10        hda8/hd9
Fedora5       hda9/hd10
Mepis          hda10/hd11
PCLinuxOS  hda11/hd12

You can also use fdisk -l to view your partitions

Reboot into XP
Install  explore2fs  (this allows you to read linux partitions under XP)
View all linux partitions, ignore numbering as this is different under XP!
This will be useful later

Install first distro - PCLinuxOS
This is a live cd so you have to run through this first then click on the install icon on the desktop. Do not install grub/lilo to mbr.

Reboot back into XP

open explore2fs
browse to PCLinuxOS /boot
identify the filenames for vmlinuz* and initrd* - you need these to add to grub
reboot to Ubuntu

Open a terminal and type "sudo gedit /boot/grub/menu.lst"
This will open up the menu list for grub
You can back u your "menu.lst" if you want, before editing

Scroll down to below the entry for memtest and type the following:
```

title		PCLinuxOS, kernel 2.6.12-oci6
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.12-oci6.mdk-i586-up-1GB root=/dev/hda12 ro quiet splash
initrd		/boot/initrd-2.6.12-oci6.mdk-i586-up-1GB.img
boot
```
(obviously use your found file names, mine are only examples that I used)

Save and reboot. You will now see the PCLinuxOS entry in your grub menu
Try it, and if you have typed everything correctly PCLINUXOS will boot up.

Repeat this installation mallarky for each of your other distros, and repeat the menu.lst editing for each.

This all goes well until I installed SUSE10, which despite me telling it otherwise, installed its own grub to the mbr, so on boot I got its (very nice) grub menu, even though it missed tow of the distros I had installed, although fortunately ubuntu was there.

To get back to your nicely crafted ubuntu grub, boot into Ubuntu from the SUSE menu. Open a terminal and type the following:

1. (You may need to be root)

2. Open a terminal window
3. Type "grub"
4. Type "root (hd0,7)", or whatever your harddisk + boot partition numbers are
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

Your grub menu will be back with all your distros listed, ready to be booted

Thanks for all the info gleaned from ubuntu forums that helped me get to here.

Having tried out all the others, only ubuntu allowed manual configuration of network settings during install, and even though its kde, only PCLinuxOS comes close to Ubuntu for usage and functionality

---

### Post by Sbarton on 2006-04-03
Thank you both for taking time and trouble to post your suggestions this has given me a lot of food for thought. When I hit problems( and I will) I'll be back.
regards:)

---

