---
title: "Isolinux.bin missing error a Bootable USB for WIndows 7 (USB setup in 13.10)??"
date: 2013-10-30
forum: Any Other OS
---

### Post by MasterNetra on 2013-10-30
Ok so I wanted to put my backup of my windows 7 DVD back onto a USB drive I generally use for both it and Linux distros. So I formated the Drive to NTFS and set the boot flag using gparted. Then opened the ISO and dragged all the contents as usual to the Drive, this time being in 13.10. (Did it in past versions fine). Afterwards restarted and tried booting from it to test it and surprisingly got a isolinux.bin is missing error. The ISO I know is fine and even if it wasn't that error I would think shouldn't be there still. Tried reformating the USB drive again, flagging it, and even made a new iso from DVD for the heck of it and still same weird error. Any thoughts?

---

### Post by oldfred on 2013-10-31
Moved to Other OS.

Windows needs a Windows boot loader in the MBR, but many of the generic boot loaders like syslinux or lilo will work. But Windows also needs the PBR or partition boot sector to have boot code also. Gparted creates a XP boot as default. You may have to run chkdsk from Windows 7 to fix the PBR.

       Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

