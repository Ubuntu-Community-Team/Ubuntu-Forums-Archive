---
title: "Easy Peasy on ASUS eee 701 4G"
date: 2012-05-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tzinck on 2012-05-18
I would like to install Easy Peasy on SD cars on an eee 701. It installs but will not boot afterwards (I have changed boot priority right in bios). Easy Peasy runs well on it if I install on internal 4 GB "hdd" - But I would like more space so I install on 8 GB SD card.
 
Any suggestions on howto handle this ?
 
I dont mind running from USB stick either, but I need it to be real installation - not only trial. I am open to alternative suggestions

---

### Post by Plumtreed on 2012-05-18
When installing you need to select Grub in order to be able to choose which 'disk' to boot from.......after install, boot, and when you see the 'Asus' screen press 'Esc' to cause the boot choices screen to appear, then select.

Easy Peasy was a very appealing OS for eeePC701s but I don't think it is still active:confused:

---

### Post by dalee on 2012-05-19
Hi,

EasyPeasy is at 2.0 Alpha based on 12.04 right now. So it would appear to be still viable. 

I'm not a fan of Gnome Shell though. I prefer either XFCE or Unity 2d on my 1101.

dalee

---

### Post by davidm49 on 2012-05-25
> **tzinck said:**
>  It installs but will not boot afterwards (I have changed boot priority right in bios).

Two possible causes are worth some investigation.

1. After a few years of use, the SD card slot in the 701 starts making write errors that can corrupt any OS installed on the card. I used to have EasyPeasy running from an SD card plugged into the card slot. Now it will not work that way. Instead, I have to put the card in a USB card reader and plug that into the 701.

The write errors can happen during installation of the OS. It is possible that the installation was not in fact successful, even if it seemed to be. However, before you install all over again into a card in a USB card reader, you might read the next paragraph, since that describes a different possible cause that is quicker to fix.

2. You mention that you have changed the BIOS so that it points to the SD card. The BIOS ought to point to the drive where you have GRUB installed, and then you choose from the GRUB menu which OS you want to boot. Did you install GRUB on the SD card as well as on the internal SSD/HDD? Whether you did or not, you should try the following procedure.

Make the BIOS point to the internal drive again. Boot the OS on the internal drive. With the SD card attached, open a terminal and run: ```
sudo update-grub
sudo update-grub2
``` (I always run "sudo update-grub" as well as "sudo update-grub2". It's probably unnecessary, but it does no harm, and I have never seen a definitive statement that "update-grub" is now redundant.)

Reboot, without changing the BIOS (i.e. it still points to the internal drive). You will find a menu, offering a choice of operating systems. Select the OS on your SD card. If it is not offered on the menu, there is something wrong with the installation.

---

