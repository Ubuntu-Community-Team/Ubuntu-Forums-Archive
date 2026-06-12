---
title: "Where can I find a boot disk forUbuntu..?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by TroyR on 2007-01-08
I'd like to dual boot Xandros and Ubuntu but cannot find a boot disk. Xandros is already loaded . Do you think Ubuntu will partition the drive OK..?

---

### Post by anaconda on 2007-01-08
Yep. Ubuntu will install "OK".. whatever that means..

But after installing ubuntu you propably have to add Xandros to the grub-bootloader which  ubuntu installer installed. (windows is detected and added to grub automatically)

If you type this in terminal you can edit grub
sudo gedit /boot/grub/menu.lst

If xandros uses grub you can just copy the lines to your new grub.. or reinstall the bootloader which xandros uses and add ubuntu to it.. (ubuntu installer will overwrite your mbr and install grub to it.. unless you install from alternate CD)
You will find lots of help from these forums.

You wont need boot disks once you got the bootloader working... Cant help with those, because I haven't made any yet..

---

### Post by TroyR on 2007-01-09
Jeez, I guess I'll just stick with Xandros...

---

