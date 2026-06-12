---
title: "new install of ubuntu studio won't boot"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-16
I have just finished an installation of ubuntu studio, only other os on the PC is XP, and it went happily all through the installation and exited normally, with a ' well done and welcome.' message. . On reboot however, after the grub choice, I get a splash screen, a very long wait, and then it hangs with the following message


BusyBox v1.1.3 (debian 1:1.1.3- 3ubuntu3 ) Built in shell (ash)
Enter help for a list of built in commands 

/bin/sh: can't access tty: job control turned off
(initramfs)


any ideas? Thanks

---

### Post by ginestre on 2007-05-16
Further information, if relevant: if I boot from the install DVD again, it all loads up quite happily and I can browse between the verious partitions on the HD. But If I boot from the installed version, using the repair option from the GRUB menu, I alwasy get a message saying hda6 was last mounted in tghe future, and the problem has been FIXED. But this FIXED doesn't last through to the next boot, when the same message comes up again.

Is theer some way to scroll through the reams of stuff the repair option spews out, so see f something or other didn't work properly? And how do I get from a terminal in repair to a graphical interface?

---

### Post by ginestre on 2007-05-16
OK, so using the repair option left me in a terminal, and I found that if I did startx I got into the graphical environment; but I can only see the root partition as well as the winXP partition, and neither of the other partitions where I put home directory etc. If I go HOME I finish in /root.

Also, though this was a ubuntustudio DVD install, the software installed is exactly the same as the ubuntu I have on my oither PC. So obviously I did something wrong- but what?

---

