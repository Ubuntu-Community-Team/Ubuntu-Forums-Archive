---
title: "Please Help me with my 1st Gen Mac Pro"
date: 2017-01-05
forum: Apple Hardware Users
---

### Post by martyfree123 on 2017-01-05
I have a 2006 Mac Pro and I have followed the guide on fixing the EFI boot and all but I have one problem that prevents me from doing all this. My Mac won't boot from the USB Installer drive! I have a 14.04 LTS install drive that works great on my 2010 MacBook but the make pro doesn't display the "EFI Boot" option in the "Alt/Option" Boot menu. Any help would just be amazing! Thank you in advance!

---

### Post by yaboo on 2017-01-07
Hi

You need the amd64+mac iso image specifically for the  macpro 1,1 or 2,1. For some reason the desktop version does not work at the grub installation procedure. Usb installation does not work unless you make a special boot usb. I had to install the server version then upgrade to the desktop version. When you upgrade from 14.04 to 16.04 version, remember to install "noefi" in the grub file, or the macpro 1,1 will not reboot. You can use certain pc card. I have a nvidia 570gtx in mine at the moment.

---

