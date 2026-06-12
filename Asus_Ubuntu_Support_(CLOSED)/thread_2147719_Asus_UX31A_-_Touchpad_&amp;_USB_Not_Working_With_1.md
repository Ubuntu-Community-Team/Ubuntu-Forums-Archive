---
title: "Asus UX31A - Touchpad &amp; USB Not Working With 13.04 Install - Work with USB Live Boot"
date: 2013-05-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Prebot on 2013-05-22
Hi,

I recently picked up a UX31A (non-touch) and installed x64 13.04 from a UEFI booted USB drive.  Using the USB drive as a live instance, the pointer and USB devices work fine.  However, after the install (and boot repair) the touchpad doesn't work and plugging in a USB mouse (or any USB device) doesn't work either.  I've tried every combination of BIOS settings I could think of and nothing seems to enable the touchpad and USB.  I followed the directions at [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime) and have flashed the latest BIOS 218.  

Has anyone else had this problem and found a solution or have any suggestions?

Thanks!

---------------------------------------

For posterity's sake, the laptop had a refurbish W7 MBR install, wiping that out and going with a fresh USB UEFI Windows 7 install to be in GPT mode, then shrinking the partition and installing Ubuntu off a EUFI USB boot worked.  I had to pick a 'something else' install, but it correctly added a EFI ubuntu entry so I can pick the boot target w/ ESC at startup.

---

### Post by digitaleagle on 2013-05-28
What did you use to create the USB drive?

I had the exact same problem with my laptop.  I ran across Husain's Chronicle where he mentioned that everyone who used UNetbootIn to build USB key installation media had this problem.  It seemed strange to me that the USB Live Image would work fine but the install would break.  Still, when I went back and used a different program to copy the ISO to the drive and reinstalled, it worked fine for me.

I hope that fix works for you, too.

Here's Husain's article:
[http://blog.husainad.com/installing-ubuntu-13-04-mouse-touchpad-not-working/](http://blog.husainad.com/installing-ubuntu-13-04-mouse-touchpad-not-working/)


Here's my experience if it helps:
[http://linuxsagas.digitaleagle.net/2013/05/28/ubuntu-13-04-a-ruckus-with-ringtail/](http://linuxsagas.digitaleagle.net/2013/05/28/ubuntu-13-04-a-ruckus-with-ringtail/)

---

### Post by gsoundsgood on 2013-09-09
Hi there!

I've installed ubuntu 13.04, livedisk made with unetbootin, on an asus n53sv... everything is working fine, except for the two left and right buttons of the touchpad. tapping on the touchpad works, using a usb connected mouse all works fine. I really don't want to re-install from scratch just for this issue...

---

