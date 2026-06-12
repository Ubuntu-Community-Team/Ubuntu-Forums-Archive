---
title: "Macbook 1.1 with new  Lubutu 18.04 LTS won't boot without &quot;Options&quot; key being pressed"
date: 2020-04-16
forum: Apple Hardware Users
---

### Post by nola-guy on 2020-04-16
While trying to do a live boot into various versions of Linux I kept having issues with a dead keyboard keeping me from making selections necessary to boot from the cd. I attempted to follow a suggestion from this forum to press "1" early in the loading process and to then hold down "Enter". This seems to have corrupted something in the boot loader, since it caused the above problem. I have since installed Lubuntu, and the computer works fine, except that I have to hold down the options key to get it to boot.  If I don't push "options" to get to the boot menu I get a file folder with a "?", which I understand means it's missing some file for the boot loader. How can I correct this? I also can't get into the bios, or recovery mode. None of the key combinations used during boot have any effect, except for the "options" key mentioned earlier.

---

### Post by gsahli on 2020-04-18
I'm pretty sure that grub hasn't been installed in the right place (needing to use the Mac's built-in boot loader is the clue).
The first thing you can try is auto-installing grub using the command -
sudo update-grub
If no help there, read through this:
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by nola-guy on 2020-04-19
The shutdown may delay fixing this since I set up the comp for a senior, and her building is on lock-down and Teamviewer stopped working.

---

### Post by nola-guy on 2020-04-19
Do I need grub when the system only uses Linux?

---

### Post by CelticWarrior on 2020-04-19
> **nola-guy said:**
> Do I need grub when the system only uses Linux?

YES, yes you do.

---

