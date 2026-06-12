---
title: "Killed grub bootloader.. cant get out of windows ahhh"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by g3k0 on 2007-01-27
I just formatted my windows partition and reinstalled it.  Somehow I managed to kill the grub bootloader or pixiebooter or whatever you want to call it.  Now it only boots to windows.  My linux partition is still there I can see it when I go into Disk Management.  I just dont know how to access it.  Any help wouild be appreciated.

---

### Post by xpod on 2007-01-27
This is the easy way of doing it i believe

[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub)

---

### Post by tkjacobsen on 2007-01-27
This is a common problem with windows. It is not tolerant about other operating systems...

Make yourself a grub boot disk and boot manually into ubuntu. (This can be done from some live-cds. Don't remember if you can use the ubuntu live cd) Then type in terminal

sudo grub-install hd0 

this will (re)install grub to the master boot record.. Remember to add windows to your /boot/grub/menu.lst. Examples are given in the file. (Just use chainloader +1)

---

### Post by g3k0 on 2007-01-27
Well I dont have a floppy drive so i used live and this command 
sudo grub-install hd0 

gives me
Could not find device for /boot: Not found or not a block device.

---

### Post by tkjacobsen on 2007-01-27
Did you boot properly into your existing ubuntu installation?

---

