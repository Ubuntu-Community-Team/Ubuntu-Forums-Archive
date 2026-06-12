---
title: "Dual boot won't boot xp or Ubuntu"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by eduardoeltortuga on 2007-04-21
I recently lost power to my computer. In the process of testing out different reasons, I cleared my CMOS. I had to replace my power supply but I am not able to boot XP or Ubuntu. I can only get as far as the grub menu.
          
                      Thanks for any advice:confused:

---

### Post by cypherzero on 2007-04-21
Use the Ubuntu Live CD to start Ubuntu.
Reinstall GRUB from there, something like:

[FONT="Courier New"]sudo grub-install --root-directory=/whatever/boot/grub /dev/hda[/FONT]

---

### Post by oilchangeguy on 2007-04-21
what do you mean you cleared the CMOS? all you should be able to do is reset it to default. even if you remove the mobo battery, it will restore the default settings.

---

### Post by Doug11 on 2007-04-21
Here is a good guide to reinstall grub from live cd

[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

---

### Post by eduardoeltortuga on 2007-04-21
Wow! Response time for my problem was VERY fast! Thanks. I will reintall the grub menu

            Ubuntu to all and to all a good night:)

---

