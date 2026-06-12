---
title: "Cant boot into Windows XP or Ubuntu 7.10"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by BloodCloak on 2008-01-21
I have Windows XP installed on my C: drive and had a D: drive that i used to keep my other data on. I decided to install Linux on it and made the mistake of installing PCLinuxOS on it. I resized the D: drive and made the 3 partition linux needs (/, /home and the swap partition). It all worked well but i decided PCLinuxOS wasnt for me and decided to install Ubunutu 7.10 86-64 over it.

I installed it into the the partitions the other Distro used (after formatting them) and installed GRUB. Now when i start up the computer grub loads but when i select the Ubuntu OS it says that the partition cannot be found and when i select the Windows OS it says that "NTLDR cannot be found press Ctrl + Alt + Delete to restart the computer" (This also happened with the old Distro but there were 2 Windows option Windows which caused the same thing and one called "windows1" which loaded windows normally, but i dont have the second option anymore)

Please Help

---

### Post by A4006 on 2008-01-21
Do you have one SATA drive and another IDE drive, and your SATA drive is the primary boot drive?  I ask this because Ubuntu likes to think that the IDE drive is the primary one, no matter weather is is or not, and installs GRUB on it, leaving the BIOS default drive without GRUB or a corrupt version of it, perhaps left over from your PCLinuxOS install.  If this is the case, then changing the order of the drives in the BIOS (IDE first) and reinstalling the windows bootloader to your C:/ drives' MBR would work.  Please be waned that resetting the MBR to windows would make it so you would not be able to boot into Ubuntu without reinstalling GRUB, and I do not recommend it unless it is the only other option.

---

### Post by BloodCloak on 2008-01-21
My windows drive is an IDE and my D; drive is a SATA. Ubuntu and PCLinuxOS both tried to install to D: by default but i changed both of them to install the boot loader on C:

---

### Post by jerrykenny on 2008-01-21
yes, the bootloader should be on C.

Can you boot into your installation cd by typing "rescue" at the cd prompt ?

Youll need to know the name of your ubuntu installation ( /dev/hdd?) the  / file system.

If you can log in this way, try typing 

[SIZE="3"]grub-install  /dev/hda[/SIZE]

you'll need root privelidges

---

### Post by BloodCloak on 2008-01-22
> **jerrykenny said:**
> yes, the bootloader should be on C.

Can you boot into your installation cd by typing "rescue" at the cd prompt ?

I dont know what that is / how to do it but if ,through the ubuntu live cd, i type "sudo grub-install /dev/hdb" it says "/dev/hdb does not have any corresponding BIOS drive". Also if i type ""sudo grub-install /dev/sda7" (My / partition) its says that a boot device could not be found for it.

EDIT: could it have anything to do with the fact that i have a /, /home and swap partition but no /boot partition

---

### Post by h84ll1 on 2008-01-22
Super GRUB can be useful in fixing these issues. It's a live CD too so.  I have my drives the opposite way round to you, but installed Ubuntu on a partition on the windows SATA drive.  It put the bootloader onto the IDE so then it didn't work.
Super GRUB will almost definitely get you back into Windows again, did for me.  Then i decided i'd reinstall without the other drive complicating things.

You could use super GRUB to get into windows and format the other drive to start again if needed.

Not sure how to make it install the bootloader on the drive you specify, but sounds like you knew how to do that.

Hope this helps a bit, even if it's just for super GRUB.
Good luck with it!

---

