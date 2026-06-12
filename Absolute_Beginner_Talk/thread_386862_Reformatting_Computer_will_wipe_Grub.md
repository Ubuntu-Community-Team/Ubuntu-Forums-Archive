---
title: "Reformatting Computer will wipe Grub?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by cgreer on 2007-03-17
Hello,
   I've just gotten edgy to where I want it (with beryl and a lot of custom stuff on it) but I want to reformat my windows partition because it has "slowed down".  I've reformatted my computer gobs of times but never with linux on its own partition.  After I reformat the windows partition will it reinstall its own bootloader?  How do I get grub back so I can access my linux partition if it does?

Thanks a bunch!

---

### Post by AtrejuT on 2007-03-17
well just reformatting the drive will not install any bootloader whatsoever, and leave grub well alone if it is sitting in your mbr.
But if you not just format it but reinstall it then windows will overwrite grub, I think.
You then have to boot a live CD and get grub back in order.
That doesn't mean you have to reinstall ubuntu, though, it will just stay as it is (as long as you don't format the Ubuntu partition ;-) )

atreju

---

### Post by cgreer on 2007-03-17
So with they Live CD in, I click install and when I get to the part where I manually edit the partition tables I just leave everything blank?

Thanks for the help

---

### Post by annda on 2007-03-17
no, you will need to run the live CD (don't go to install) and then issue some commands in the terminal.

take a look here, it's pretty easy:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by louieb on 2007-03-17
Just reformatting your windows partition should not bother GRUB or Ubuntu.
Its when you reinstall XP, it will modify the MBR of the drive to point to the windows boot loader, NTLDR. 

After reinstalling XP then it time to change the drives MBR back to pointing to Ubuntu's GRUB boot loader.  For the tried and true method of doing just that see the Reinstall GRUB link in my signature. (same one suggested by annda).

---

