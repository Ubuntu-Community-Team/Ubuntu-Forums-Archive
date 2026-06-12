---
title: "GRUB does not display."
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by xioSlayer on 2008-02-06
I've installed ubuntu on a second hard drive, and I cannot figure out how to boot it.  Here is my layout:

200GB HDD - Windows XP
200GB HDD - Where I tried to install Ubuntu
500GB HDD - Storage

How can I correctly configure GRUB?  I read a post about reinstalling GRUB from the live CD, and performed the steps, but I still had no luck.  Help would be appreciated, thanks.

---

### Post by Origin415 on 2008-02-06
What drive is grub installed on?

Your computer is probably booting up from the first hard drive, if grub isnt there, itll go right to windows.

Check if you can change the boot order in your motherboard's BIOS settings (when you boot up, it should display a special key to hit to get into the menu), otherwise you will need to install grub manually on the first hard drive.

---

### Post by xioSlayer on 2008-02-11
> **Origin415 said:**
> What drive is grub installed on?

Your computer is probably booting up from the first hard drive, if grub isnt there, itll go right to windows.

Check if you can change the boot order in your motherboard's BIOS settings (when you boot up, it should display a special key to hit to get into the menu), otherwise you will need to install grub manually on the first hard drive.

GRUB is installed on (hd0).  I tried installing it there manually after the installation did not work via the grub> prompt.  What should I do?

---

