---
title: "Dual-Boot + Windows Vista"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by kc0eak on 2006-09-16
Hello,

I am currently dual-booting my laptop with Windows XP and Ubuntu.  I am using the GRUB boot-loader.  I just downloaded the new Windows Vista RC1 and I was considering trying it out.  I don't want to replace my current Windows installation, just try out the new one.

XP and Ubuntu are loaded on my internal hard drive.  I'd like to load Vista onto my external drive so I don't mess with anything on the internal one where all of my files are.  How do I get Vista to show up in the GRUB boot-loader menu once it is installed, and will Vista mess up the GRUB menu?

Thanks

---

### Post by JayTee on 2006-09-16
> **kc0eak said:**
> Hello,

I am currently dual-booting my laptop with Windows XP and Ubuntu.  I am using the GRUB boot-loader.  I just downloaded the new Windows Vista RC1 and I was considering trying it out.  I don't want to replace my current Windows installation, just try out the new one.

XP and Ubuntu are loaded on my internal hard drive.  I'd like to load Vista onto my external drive so I don't mess with anything on the internal one where all of my files are.  How do I get Vista to show up in the GRUB boot-loader menu once it is installed, and will Vista mess up the GRUB menu?

Thanks

Vista should only kill grub if it's installed on the same hard drive as Ubuntu. I would set your BIOS boot order to boot first to DVD drive, then to the USB drive for the Vista install. Once you get Vista up and running then set the BIOS back to boot to the primary internal drive. Then edit your grub menu.lst file to add the Vista drive and partition.

To edit GRUB's menu do this:
open a terminal window
type the following
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
"this makes a backup copy of the menu"
then type this:
sudo gedit /boot/grub/menu.lst
in gedit add the following lines after the
###END OF AUTOMAGIC KERNEL line.

title     Windows Vista RC1
root      (hd#,#) 
makeactive
chainloader +1

NOTE:
for the root statement where # is the the hard drive device number in Ubuntu use the number of the device for the USB drive and the number of the partition. This number system starts at zero so (hd0,0) would be the first hard disk on the system and the first partition on that drive and so on. I forget the command to list the device numbers of the drives on a system but on a laptop that has one hard drive then your external USB drive should be hd1. If you setup only one partion on it for Vista then the root statement in the menu.lst file would read 
root      (hd1,0)

if booting to Vista fails then try increasing the hd number to 2 as the cdrom drive might be grabbing device number 1. Not sure since I'm still a newbie to Ubuntu and grub but I've learned alot getting dual boot working on a single drive. Separate drives are easier it seems.

Best of luck

---

