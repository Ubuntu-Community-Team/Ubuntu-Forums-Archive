---
title: "Error 22 : no such partition when dual booting."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Tipharet on 2007-04-21
Alright so this is my first time delving into linux. I have ran the live cd and manually partitioned to the follow:

> /dev/sda

/dev/sda1 NTFS /media/sda1 196263mb (windows partion)

/dev/sda2 ext3 / 52765mb

/dev/sda3 swap 1024mb

I follow it through, click advanced and put /dev/sda2 to install the bootloader on that partition. It installs successfully. I reboot, it totally skips the linux parition boots in to windows. I uses Easybcd and create a linux boot choice. I reboot, I select the ubuntu options and it brings me the linux grub where I select which kernel I would like. I select the ubuntu kernal and it gives me an error 22: no such partition.

I have used grub to find out where the boot loader is and it tells me (hd0,1). If I am not mistaken, that would be the master HDD on the IDE channel partition 1. Why did it install the bootloader to that partition? 

Did I not type the correct install path for advanced in the bootloader install option? I want to install this on my SATA drive, on sata port 3, on partition 2. Which if I am not mistaken should be (sda2)? When I tell it to install in that format, it gives me an error stating it cannot install the boot loader.

Is there anyway to use grub in the terminal to change where I told it to install the bootloader?


Edit: heres my thread on hard forum, probably explaining the individual issues in more detail.

[http://www.hardforum.com/showthread.php?t=1182397&page=1](http://www.hardforum.com/showthread.php?t=1182397&page=1)

---

### Post by BoneKracker on 2007-04-22
For one thing, there is no such device as /dev/sda,2
The comma is extraneous.

You might want to refer to the GRUB documentation to verify your install location format (sda,2).

[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

---

### Post by Computer Guru on 2007-04-25
We rewrote the [Linux Documentation](http://neosmart.net/wiki/display/EBCD/Linux) for [EasyBCD](http://neosmart.net/dl.php?id=1) with new instructions on detecting the correct drive and installing GRUB to the bootsector of the partition in a manner that's compatible with the Windows Vista BCD bootloader and EasyBCD-ready.

The new docs should do exactly what you need :)

---

