---
title: "LILO problem"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by nicotineman on 2006-02-22
Hello. I am an unashamed noob, and would be very grateful for your help.

I want to dual boot Ubuntu and XP, but I don't want to touch my MBR or XP bootloader as I've had some disasters doing this in the past. From reading around, the best way I can see of doing what I want is to boot from a GAG boot floppy and install the LILO bootloader to my Ubuntu partition.

However, when installing Ubuntu, the installer cannot install LILO. I choose not to install GRUB, to install LILO and to install to my new Ubuntu partition (/dev/hda2). Error message:

Running "/sbin/lilo" failed with error code "1"

Obviously I can't boot to Ubuntu without a bootloader. Where am I going wrong please?

---

