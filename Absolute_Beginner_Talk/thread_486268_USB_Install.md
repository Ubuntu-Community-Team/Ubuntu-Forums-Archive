---
title: "USB Install"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by G-Diggers on 2007-06-27
Hi Again
I have 2 questions this time. Question 1: I want to do a USB install on an 80 Gig HD. I fond directions on here but is says to do a Manual Install. How in the world do I do that?:confused: When I hit the install on the live CD it just installs I can direct it to the USB Hard drive But I can't seem to get the grub there. Question 2 is If I have it installed on the USB Hard drive already Can I just install Grub with out doing a complete install again?

Thanks in advance!

---

### Post by G-Diggers on 2007-06-27
I actually have the Live cd in and the USB drive connected and can go into it look in the Boot folder and there is a Grub folder. Is there something in that that I need to change  to get this to work?

---

### Post by logos34 on 2007-06-28
> a Manual Install. How in the world do I do that? When I hit the install on the live CD it just installs I can direct it to the USB Hard drive But I can't seem to get the grub there. Question 2 is If I have it installed on the USB Hard drive already Can I just install Grub with out doing a complete install again?

Before you begin the install, enter the BIOS and set the usb drive to first position in the **hard disk boot order**. The cdrom should be set as the first boot **device** so you can boot the install cd.

Once you have begun the install you will come to a screen with an option to "manually edit partition table."  After you have gone through the steps of creating a / and /swap partition and associated mount points for them, you will arrive at a 'ready to install' screen.  Click on the 'advanced' button at the bottom.  In the grub dialog box that opens specify where you want grub written: take out '(hd0)' and replace with  '/dev/sda'.  Use '(hd0)' only if you are sure that the usb drive is being seen as the first BIOS boot disk.

yes you can install grub without doing a full reinstall of the OS.



[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://img519.imageshack.us/my.php?image=feistydual18cv5.png](http://img519.imageshack.us/my.php?image=feistydual18cv5.png)

---

