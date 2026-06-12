---
title: "Dell dimension 3100 boot up problems"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by manij on 2007-01-05
I'm trying to run Kubuntu on my dell dimension 3100.

I install it on a ide hard drive attached as a slave in CDROM ide port/connection.

The installation goes w/o any problem.

however when I try to reboot, the kubuntu installation is not being recognized. This is the cae even when I adjust the boot sequence in the bios to be first one to boot from the ide drive.

the problem doesn't go away even if I disconnect my SATA drive. I just the response back indicating there is no boot drive.

Here is what sudo fdisk command outputs!

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 4813 38660391 83 Linux
/dev/hdb2 4814 4998 1486012+ 5 Extended
/dev/hdb5 4814 4998 1485981 82 Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 4 32098+ de Dell Utility
/dev/sda2 * 5 14179 113860687+ 7 HPFS/NTFS
/dev/sda3 14181 19022 38893365 7 HPFS/NTFS
/dev/sda4 19023 19452 3453975 db CP/M / CTOS / ...

As you can see the kubuntu installation is in the smaller HD.

What am I doing wrong.

Thanks
Mani

---

### Post by mahy on 2007-01-05
Can you boot another HDD? Well, put GRUB in there and let it boot whatever you like. I've never messed with bootup sequences, it's pretty useless

---

### Post by manij on 2007-01-05
Can you expand on that bit?

what exactly is GRUB? how do I let it chooose which one to booot?

mani

---

### Post by moshuptrail on 2007-01-05
grub is the boot loader supplied with Ubuntu.  It presents a menu when you boot allowing you to boot whichever hard drive you choose.  When you installed Kubuntu it should have given you the option to install a dual boot capability.  

There is a way to install grub later, but someone else will have to explain that.

---

### Post by nick944 on 2007-01-05
What's funny is that any problem at all with a computer is usually a problem with a dell :mrgreen:

---

### Post by manij on 2007-01-06
It says the GRUB will be installed in hd0. I'm not sure which drive that is! Can so one help how to install it in the right place?

Mani

---

### Post by mahy on 2007-01-06
Given that Ubuntu is already installed somewhere, just put the disks into the original boot order and boot the computer with Ubuntu Live CD.

This is GRUB nomenclature:

(hd0,0) - disk one partition one
(hd0,1) - disk one partition two
(hd1,0) - disk two partition one
(hd1,1) - disk two partition two
etc...

When Ubuntu boots, do this:

sudo mkdir /mnt/foo
sudo mount -t [filesystem_type] [disk_with_ubuntu_installation] /mnt/foo
sudo chroot /mnt/foo
sudo grub-install (hd0,0) <-- to install it on the first drive

then you may wanna check /boot/grub/menu.lst, which is its config file. It should have entries for all you OSs. That's it! After reboot, a GRUB screen will show up and you'll have to select an OS you want to boot. Good luck!

---

