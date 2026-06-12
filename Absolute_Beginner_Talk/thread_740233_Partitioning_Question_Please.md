---
title: "Partitioning Question Please"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by bobnutfield on 2008-03-30
Hello Everyone,

I have a new Toshiba laptop and want to install Gutsy, but it will not recognize my wireless or sound (from the live cd.)  I may be able to resolve these issues as I have done quite a bit of reseach on the subject.  But for now, I have to keep Vista (which I am not familiar with) and will need to dual boot.  

As usual, there is a recovery partion on this 80GB drive of 5GB in size, then the 34GB Vista Partision and one of 35GB called "Data" with only 85mb used.  Gparted in Gutsy shows these as
sda1, sda2, and sda3.

My question is, since obviously sda3 is the installation partition I intend to use, does anyone know the effect deleting this partition will have on Vista?  I will eventually wipe Vista, but I can't until I get the wireless and sound issues sorted.

Any replies are greatly appreciated.

Regards

Bob

---

### Post by Duck2006 on 2008-03-30
Use the partitioning tool from with in vista to partition space for your ubuntu install, this may help.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by abhiroopb on 2008-03-30
I'm 99.9% certain that if you format the Data drive the vista partition will remain intact. Of course you will lose the 85mb of data on the partiion (so you may want to back it up).

For help on partioning and adding Vista to the Grub: [http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/](http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/)

(it is for XP, and it works, haven't tested for vista, but should be the same)

---

