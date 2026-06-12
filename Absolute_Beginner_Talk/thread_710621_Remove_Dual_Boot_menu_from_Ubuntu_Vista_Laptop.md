---
title: "Remove Dual Boot menu from Ubuntu/ Vista Laptop"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by rich_wookey on 2008-02-28
Hi

I'm an absolute Linux/ Ubuntu beginner....

I've installed Ubuntu 7.10 on a spare USB 2.5" 80GB Disk Drive on my Dell XPS M1330 Laptop.

It seems to works OK - I have a Dual boot menu (is this GRUB?) and can boot into Ubuntu or Vista (although latter is listed as XP in the boot menu!). But if the USB disk is not plugged in when I boot I get GRUB error 21. If I change BIOS boot order so that USB is at top, I get "cannot load operating System" error

However, my intention was to not have a dual boot menu, when I wanted to boot to Ubuntu, I would change the BIOS boot order to USB 1st, insert the USB disk, boot and hey presto, Ubuntu would be loaded.

Similarly, if I wanted Vista, I would simply not plug in the USB disk and boot directly into Vista, again without the dual boot menu

Question 1 - how do I remove the dual boot menu, so laptop is back to original spec and will boot directly to Vista when USB disk is not plugged in? - I think I've found the answer to this in [http://ubuntuforums.org/showthread.php?t=648747](http://ubuntuforums.org/showthread.php?t=648747), but not tried it yet

Question 2 - how do I modify the USB disk, so it will boot directly to Ubuntu, when I have it plugged in?

Many Thanks

Rich

---

### Post by zephyrcat on 2008-02-28
When you installed Ubuntu on to the USB key, GRUB (the dual-boot menu) was put onto the hard drive, instead of the USB key. To solve this problem you have to tell Ubuntu when you install it that you want to put GRUB in a particular place (the USB key.)

In order to do this, go through the installation of Ubuntu until the last confirmation screen. At this point, click "Advanced." Within advanced there is a field for "device for bootloader installation." Here you must tell the installer to install the bootloader (GRUB) to the USB drive.

Hope that helps!

---

### Post by defrex on 2008-02-28
As to the first question, you were right about that forum post. I've personally only ever done it with XP, but fixmbr should to it.

As to fixing the boot problem. You need to reinstall Ubuntu on the USB drive. On the very last step, when it goes over the details and before you press install, there should be a preferences button or something like it. In there you can select which partition GRUB is installed into. The main disk will most likely be hd0 and the second one should be hd1. If you have more then the two drives, it might be a little different.

After all that, GRUB will only load when you boot from the USB disk.

---

### Post by anewguy on 2008-02-28
I believe the error is telling you that it can't find the grub files, which would be true if the drive you installed Ubuntu on is not plugged in at the time.  What happen is that the installation changed the master boot record on your Windows disk to use grub and it expects to find grub on the usb drive.  No drive - no grub - no boot.

You basically want stand-alone operating systems on each disk.  You will need to be sure there is an MBR on the usb drive so it can load grub (currently I would suspect there isn't) - you can do this with a super-grub disk if you want.  After you get that, you'll need to boot into Windows and download a program call fixmbr.exe (it's a free download) then run it to reset the MBR on your Windows disk to load Windows only.

:)

---

### Post by rich_wookey on 2008-03-01
Many thanks for the replies - I've got my head around this now and fixed the MBR on the Windows disk - re-installed Ubuntu on the USB disk as per instructions above. The USB disk  already had a MBR, so booted. the only thing I've got to change is the disk "id" in the GRUB "boot file", on boot-up of the USB disk, it is looking for 2nd disk (which it was when I installed Ubuntu, but now is the 1st disk!)

I expect I could have done this 1st time, if I'd read some of the installation help docs!

Rich

(apologies if I've used the wrong terminology)

---

