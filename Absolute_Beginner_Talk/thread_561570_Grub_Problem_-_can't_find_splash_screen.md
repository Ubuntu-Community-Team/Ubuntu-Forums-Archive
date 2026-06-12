---
title: "Grub Problem - can't find splash screen"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by sdgreen on 2007-09-27
Feisty 7.04 on a IBM PC with 1.2 megs ram

For some reason GRUB goes through its initial two processes then exits with this error:

 Failed to read splash image ((hd2,0) /boot/grub/splash images/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

The system just quits and goes back to a re-boot sequence loop. Can not even go to recovery sequence. When using the live CD and mounting boot drive, I can confirm that the file is in /boot/grub/splash....

That file maybe corrupt, but I have no idea how to recover the file or even read the offending one, or where there may be a problem in the menu.lst (which I cannot edit (?) from the live cd.

How to fix?

---

### Post by por100pre1 on 2007-09-28
Spaces in folders and files names can be troublesome. Lets see what you got:

Use your LiveCD, and run Gparted. Try to mount your drive with it. Browse to find /boot/grub/splash images/KUBUNTU_splashscreen_blue_neon_logo_03.xpm. gz and post menu.lst.

---

