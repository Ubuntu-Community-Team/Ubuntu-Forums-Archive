---
title: "Ubuntu on USB key on intel mac - almost, corrupt?"
date: 2012-03-11
forum: Apple Hardware Users
---

### Post by Garrett_44 on 2012-03-11
Hi

I'm trying to install Ubuntu on a USB key, at the moment for an intel mac 64 bit but ultimately I'd like to get it working across macs and pcs - perhaps through separate partitions of the key if needed.

I'm following the tutorial here
[http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/](http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/)

and it looks like something is working.  The key boots into Ubuntu which gets to the desktop but it looks like it's corrupted (see attached image).  I can see the Ubuntu menus and even activate them with the mouse so I know divers are working etc. however no matter which iso I use, so far I've tried:

ubuntu-9.04-desktop-amd64.iso

ubuntu-10.04.3-desktop-i386.iso

ubuntu-10.10-beta-alternate-amd64.iso
ubuntu-10.10-beta-desktop-amd64.iso
ubuntu-11.10-beta1-desktop-i386.iso
ubuntu-11.10-beta1-desktop-amd64.iso

ubuntu-11.04-desktop-amd64+mac.iso

ubuntu-11.10-desktop-i386.iso
ubuntu-11.10-desktop-amd64.iso

 it seems to be the same from version 10 onwards (-10 doesn't boot).  It looks corrupt but I couldn't have downloaded that many corrupt iso's.  I suspect I'm doing something small wrong or missing a step.  Can anyone suggest what might be the problem here?

thanks in advance
Garrett

---

### Post by 2F4U on 2012-03-11
On the 11.10 desktop cd, when you reach the grub menu, can you press F6 and select nomodeset and see if that helps?

---

### Post by Garrett_44 on 2012-03-11
Hi

It seems to go through the grub menu very quickly and straight into Ubuntu.  All the while it looks like it does on the screenshot so very difficult to see these options.  Is there a way to do this if it's not visible? i.e. F6, arrow key down how many times and return?

thanks
Garrett

---

### Post by Garrett_44 on 2012-04-29
Kickstarting this thread again as I've not progressed any further with this.  Is the a way to set nomodese twhen you can't see the grub menu?  I.e. a keyboard command or a startup preference that can be added to a file somewhere?

Thanks in advance.
Garrett

---

