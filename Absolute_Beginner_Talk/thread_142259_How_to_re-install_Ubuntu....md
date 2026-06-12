---
title: "How to re-install Ubuntu...?"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by ElmZ on 2006-03-10
hello...

im totally newbie in Linux...just installed my Ubuntu last night together with Windows XP...but had some problems with soundz and accidentally deleted my username/usergroup....

so what i want to do is to re-install a fresh Ubuntu over the existing one...

how can i do this....tnx...

---

### Post by meborc on 2006-03-10
from bios, set your box to boot from CD... insert Ubuntu install-cd and do all the installation again... :rolleyes:

---

### Post by AtinLango on 2006-03-10
Remember when you are re-installing, at the Partitioning option, preferably choose manual partitioning, and make sure you specify to format the partition for Ubuntu i.e. make a clean install over the existing Ubuntu.

---

### Post by jaguaracer on 2006-03-27
Just to be sure: will this mess with GRUB?

---

### Post by cacahootie on 2006-03-27
[QUOTE=jaguaracer]Just to be sure: will this mess with GRUB?[/QUOTE]

Probably.  Any time there is more than one operating system or hard drive on my computer (not sure which, they're both always true), the installer will ask where to install grub.  If you've only got one disk, I suppose the answer to the question it asks would be /dev/hda or/dev/hda1 if you have a /boot partition you install grub to.  In the past, I have lost the ability to boot my computer as a result of a mis-installation of grub, but if you are careful to answer the questions correctly, you shouldn't have a problem (especially if you only have 1 HD).

---

