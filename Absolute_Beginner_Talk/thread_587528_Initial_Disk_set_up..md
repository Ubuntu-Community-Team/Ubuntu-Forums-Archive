---
title: "Initial Disk set up."
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Pinpoint Focus on 2007-10-22
I have downloaded the information onto my hard drive, used unzip to decompress the files, and burned the new disk with the uncompressed information on it.  My problem is trying to boot from that same disk to operate initially.  

Question 2.

I'm running off a laptop and want to load Ubuntu 7.1  onto a USB drive then operate with a dual boot, either from the USB drive or from the internal disk for Windows.

---

### Post by pieisgood4589 on 2007-10-22
What do you mean? "I downloaded the stuff and unpacked it..."

Secondly, DON'T PUT UBUNTU ON A FLASH DRIVE. THE DRIVE WILL MOST LIKELY BE CORRUPT. It is extremely complicated as well. Just dual-boot. Good luck!

---

### Post by nchase on 2007-10-22
I'm not entirely sure I understand your first question -- this information you're talking about, do you mean the ubuntu install image?

If you need to boot from that disc and are currently unable to do so, you might want to try looking in your computer's BIOS to see if the hard disk is set to boot before the cd-rom drive. The CD-Rom drive needs to have boot priority over the hard disk (needs to be set to boot first, probably)

second question: there are guides online to installing ubuntu to a usb drive. Just search Google. I don't know how you would set up GRUB to boot ubuntu from a usb drive, but if you just need to boot ubuntu once in a while, again, you can change the boot order in the computer's BIOS.

---

### Post by ramjet_1953 on 2007-10-22
What you need to do is to download the iso image and then burn that image to a CDROM as an iso image, not a data file.

Most burning programs have the option to burn as an iso image in one of the drop-down menus.

You should also burn the image slowly (no faster than 4X), as you can get errors burning an iso at faster speeds. 

Do not de-compress it, just burn the image.

You then boot from the CDROM and Ubuntu should come up in the LIVECD mode.

Don't forget to check your BIOS settings, to make sure that the boot order is set so that you can boot from a CDROM before your hard drive.

Regards,
Roger :cool:

---

