---
title: "Install On An External Drive"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by popup pirate on 2007-10-31
Hi Everyone,
This is the first time I have ever used Linux of any description so please make any replies very simple :D
I have the live version of Ubuntu 7.10 and want to put it on an external USB drive.
From what I understand, something has to go on my laptop C: drive so that I can boot into the external, once that I have it installed there.
But when I go through the install procedure I am not given the option of installing onto my F: (external drive)
Could anyone be kind enough to explain how I do this. 

Many Thanks

---

### Post by macogw on 2007-10-31
C: and F: are Windows names.  Your internal hard drive is probably /dev/sda and your external is probably /dev/sdb  On the last page of the installation, it lets you choose where to install GRUB (the bootloader).  I suggest installing GRUB on the external drive (it might call that hd1 while internal is hd0) because the GRUB menu will be on the external drive regardless of what you do, and if the external's not plugged in, the internal won't be bootable while you have GRUB on the internal with the menu on the external (I've done this).  What you should do is put GRUB on the external then when your computer is booting, there should be a "boot menu" option (F12 maybe?) that you can choose "USB hard drive" if you want Ubuntu.  If your computer doesn't offer boot menu at startup, you can set the BIOS to boot from USB hard drive before internal hard drive so that it uses the external if it's plugged in and the internal if it's not.

---

