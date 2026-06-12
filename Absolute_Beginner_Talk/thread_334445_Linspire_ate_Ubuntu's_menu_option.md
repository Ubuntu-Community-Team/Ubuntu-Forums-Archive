---
title: "Linspire ate Ubuntu's menu option"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by wamaruna on 2007-01-08
I'm pretty new to Linux.  The Mrs. bought me "Linux for Dummies" for Christmas, and it came with a DVD full of distros.  I took a 40 GB HD and wiped it clean and using BootItNG, I created an extended partition (no primary) with four predefined logical drives - a small one for Swap, and the rest equally divided over three other Linux partitions.  I successfully installed Fedora Core 5.0 to hda5, and ditto for Ubuntu 6.06 (Alt. Installation CD) on hda6.  Both use Grub.  Then I made the mistake of installing Linspire to hda7 (swap is on hda8).  Linspire 5.0 also uses Grub.  Now I have Linspire's menu which shows Linspire and Fedora, but not Ubuntu.  Any idea on how to get Ubuntu back?  Can I just reinstall Ubuntu on top of itself?  I'm no command line expert, so if I have to do something there, please explain in detail.  I appreciate any help.

---

### Post by yager on 2007-01-08
You could boot into Linspire and navigate to the /boot/grub directory and edit the menu.lst file to add the menu items for Ubuntu.

I am using Edgy Eft and here are the menu lines from my menu.lst file.
> title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot


In your case, the (hd0,0) lines will need to be changed to match your Ubuntu drive.  It is most likely (hd5,0).  You will also need to correct the root= to root/dev/hda6 since you said that you put Ubuntu on hda6.

---

