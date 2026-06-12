---
title: "Booting problems"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by juantovarm on 2007-04-23
Hello! I did a fresh install of Kubuntu 7.04 last friday, first with the live cd and then i saw it took for ages to reboot after installation. I decided to eliminate that install and reinstall it via alternate TEXT mode. Well, same problems. I decided to edit the /boot/gub/menu.lst file and delete the "silent" and "splash" options. On bootup i got this problem:

ATA 2.01 configured for UDMA/66
ATA 2.00 failed to recover some devices 
ATA 2.01 failed to set xfermode (err_mask)=0x40

It just keeps looping until it kills the process and then it continues to boot.
Any ideas?

---

### Post by Kobalt on 2007-04-23
Did it complete the install or did it stop at the beginning or during ?
Instead of removing the *silent* and *splash* options I guess you could have tried to add the *noapic nolapic* ones.
Press Ctrl+Alt+F1 to access a command line if you can and log in. From there, you can edit your /boot/grub/menu.lst file with ```
sudo nano /boot/grub/menu.lst
```
You can specify these options at the install boot screen by pressing F6 and adding them at the end of the line, then press Enter to start the install process.

---

### Post by juantovarm on 2007-04-23
I am going to go back to 6.10 and update to see what happens

---

