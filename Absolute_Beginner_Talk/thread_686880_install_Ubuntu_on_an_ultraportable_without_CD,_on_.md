---
title: "install Ubuntu on an ultraportable without CD, on blank hard drive"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by hoverdonkey on 2008-02-03
Hi


I have a Dell Latidude C400 'ultraportable' laptop (with no CD drive), on which hard drive failure is imminent.  I have a spare, healthy, blank 2.5" drive on which I would like to install Ubuntu and use in the Dell.  Can I install Ubuntu on this without CD, i.e. without having to buy the proprietry Dell CD drive and cable ?  I  looked at the forum and saw 'UNetbootin' - but this seems to be based on replacing an OS that is already installed on a hardrive.    I do also have a Windows desktop and USB 2.5" harddrive caddy if that helps. 

Any advice much appreciated!


Thanks

---

### Post by logos34 on 2008-02-03
Connect the spare drive to the Dell with the usb enclosure, download the ubuntu .iso with UNetbootin, tell it to create partitions on the usb drive and install there.  Make sure to install grub bootloader to the external drive, (hd1).  Swap out the internal drive, and reboot.  On the ubuntu kernel press 'e' to edit, 'e' again on the 'root' line and change from (hd1,x) to (hd**0**,x), press 'enter' and 'b' to boot.  Make the change permanent by y editing 'groot' and root lines in menu.lst:

gksudo gedit /boot/grub/menu.lst

---

### Post by gn2 on 2008-02-03
You should be able to get a cardbus CD-Rom drive cheap on eBay: [http://cgi.ebay.com/New-24X-EXTERNAL-MOBILE-SLIM-PCMCIA-CD-ROM-BOOTABLE_W0QQitemZ180212961387QQihZ008QQcategoryZ42180QQrdZ1QQssPageNameZWD2VQQcmdZViewItem?_trksid=p1638.m122](http://cgi.ebay.com/New-24X-EXTERNAL-MOBILE-SLIM-PCMCIA-CD-ROM-BOOTABLE_W0QQitemZ180212961387QQihZ008QQcategoryZ42180QQrdZ1QQssPageNameZWD2VQQcmdZViewItem?_trksid=p1638.m122)

---

### Post by stalkingwolf on 2008-03-05
> **gn2 said:**
> You should be able to get a cardbus CD-Rom drive cheap on eBay: [http://cgi.ebay.com/New-24X-EXTERNAL-MOBILE-SLIM-PCMCIA-CD-ROM-BOOTABLE_W0QQitemZ180212961387QQihZ008QQcategoryZ42180QQrdZ1QQssPageNameZWD2VQQcmdZViewItem?_trksid=p1638.m122](http://cgi.ebay.com/New-24X-EXTERNAL-MOBILE-SLIM-PCMCIA-CD-ROM-BOOTABLE_W0QQitemZ180212961387QQihZ008QQcategoryZ42180QQrdZ1QQssPageNameZWD2VQQcmdZViewItem?_trksid=p1638.m122)

I have 2 of these and have yet to get them to work with ubuntu (    7.04).

Do you have any links?

---

