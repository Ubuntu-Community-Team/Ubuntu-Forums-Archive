---
title: "USB Stick Boot Problems"
date: 2010-02-21
forum: Apple Hardware Users
---

### Post by mart187 on 2010-02-21
Hello,
I built an USB Stick according to [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
and also tried using the USB Stick Builder from my virtual machine Ubuntu. 
But it seems that it isnt bootable, because it isnt shown in the rEFIt boot menu. Do I make the false assumption that it should be shown there?
The disk images are MD5-verified and I tried two different USB Sticks
 Any idea how i can build a working bootable USB Stick? I need this because my CD Rom drive is broken.
My Hardware is Macbook 4,1 
Thanks

---

### Post by linuxopjemac on 2010-02-21
[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick-0](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick-0)

---

### Post by mart187 on 2010-02-21
Thanks for the link. I wont be able to use a CD since my device is broken. Also I dont want to install Ubuntu onto the stick but onto the Bootcamp partition. Any suggestions?

---

### Post by linuxopjemac on 2010-02-23
don't think a Mac has BIOS....

---

### Post by mart187 on 2010-02-23
The bootcamp partition can be booted via refit, the main problem is getting a USB Stick to boot an ubuntu live System.

---

### Post by linuxopjemac on 2010-02-23
You need at least an EFI partition on the USB stick. Make a partition of 32Mb of type FAT32 within Disk utility. The rest You can make FAT32 too I guess. From the other computer, you can then make the USB live environment with the tool you already tried on the big partition (hopefully it works that way). Then boot into OSX and copy the efi folder to the empty EFI partition according to the manual:

> -Reboot into Mac OS X.
-The EFI Boot partition should mount (as "NO NAME" in my case).
-Copy the "efi" folder to the partition.

*If needed, edit the grub.cfg file- for instance, if the Ubuntu install is not on /dev/sdb2, it needs to be changed.
**To do this: Open Terminal (/Applications/Utilities) Enter "sudo nano" and then drag and drop the grub.cfg file from the USB drive onto the Terminal window. This should give the full command "sudo nano /Volumes/NO\ NAME/efi/boot/grub.cfg." Hit enter and put in password (characters will not appear, just type the password and hit enter). The nano editor should come up to edit the grub.cfg file. When finished with any edits, press Ctrl+X, then Y (for yes), hit enter, and then hit enter again. The file is now saved with the edits.

Maybe this will help you on the way....no guarantees though

---

