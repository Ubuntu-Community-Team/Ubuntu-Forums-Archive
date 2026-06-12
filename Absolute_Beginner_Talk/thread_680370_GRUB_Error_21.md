---
title: "GRUB: Error 21"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Hitam269 on 2008-01-27
I am trying to install Ubuntu on an external USB hard drive, and I eventually got all of the installation to work.  I used the default Ubuntu installer and installed everything on the USB drive successfully, but when I restart the computer I get a Grub error 21 after the computer boots to Grub 1.5 (.  I searched google, and on pendrivelinux.com I found this advice:

> Help! I'm getting a Grub 1.5 Error 21 after a Ubuntu USB hard drive install: We received this email the other day from someone who was trying to do a full Ubuntu Linux install to an external USB hard drive. This person already had Debian Linux installed on their local hard drive and was attempting to do an install of Ubuntu to an external USB hard drive.

During the Ubuntu USB hard drive installation process, Grub was accidently moved from the internal hard drive to their external hard drive, rendering the original Linux system unbootable without the external drive plugged in. When attempting to boot from the original Debian Linux system, they would encounter the Grub Error 21 shortly after the Grub 1.5 boot process.

The good news is that the fix to repair Grub on the original system was quite simple and is illustrated below:

Reinstalling or fixing Grub after error 21:

   1. Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
   2. Open up a terminal and type sudo su
   3. Type fdisk -l and locate your Linux boot partition from the list Example: sda1 or hda1
   4. Type grub-install /dev/sdx or grub-install /dev/hdx to reinstall or repair Grub!
   5. Reboot and test!

      Notes: x represents the drive letter a, b, c, d etc. Replace with your actual drive letter.

      sdx= SATA, SCSI or USB devices hdx= IDE devices

This solution looks to me like it will work, except that I have Windows XP installed on my internal drive rather than Debian, and I don't know if Grub was installed by default on the internal or external drive.  I don't know much about linux or the master boot record or Grub, so I am just wondering if this solution will work, and if doing so will set everything up so that I can choose which OS I want to boot. Also, when I go into the BIOS settings, I don't think the boot process has any option to boot from USB drive. I could also try supergrub if I need to, or I could try to use the windows boot.ini file and load the USB drive from there, but I don't really know how to do that, so if I could get grub to work, that would be best.  Thank you for any help.

- Ethan

---

### Post by ryanVickers on 2008-01-27
You should use Super Grub Tool to restore GRUB to the main partition, and/or the MBR.  If it still doesn't work, boot the Ubuntu Live CD and change /boot/grub/menu.lst so that the partition numbers are correct.

---

### Post by Hitam269 on 2008-01-28
Thanks.  I ran supergrub, and I tried to have it fix everything itself, but I couldn't get it to work.
I was able to boot Windows XP successfully, though, which was a relief, but I could not find my Ubuntu installation anywhere.  I think the problem is that my BIOS does not load USB drives, but I'm not positive.  Supergrub showed windows at partition 2 of hd0, and it also showed an hd2, but that had no partitions.
I checked my external HD from the live Ubuntu boot and I saw that grub is installed there, so I'm not sure what part of grub if any is on my internal hard drive.  If the problem is with BIOS, how can I get around that?  Or is there some other possible problem I haven't thought of or some mistake I have made?

---

