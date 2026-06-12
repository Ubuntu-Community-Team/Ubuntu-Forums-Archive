---
title: "boot"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by cheda on 2007-02-20
I downloades ubuntu 6.10 and installed it in my home computer; in wich i have 2 hdd; i installed it in the slave drive, because if i tried to install it in another partition from the master it would freeze; i have no problems booting up to ubuntu but i can not boot to windows. i already tried to change the boot sequence on the BIOS but it alway boots to ubuntu. i tried disconnecting the slave drive and whent i start the computer i get a msg that says: error loading OS. i built the computer myself so there are no recovery discs and i seem to have misplaced the windows fuul version disc. i tried to run a repair with the windows xp upgrade disc that i have from my laptop but it will still boot directly to ubuntu; is there any way i can uninstall ubuntu


can anyone help me

---

### Post by mikewhatever on 2007-02-20
Can you please post the output of 
sudo fdisk -lu
sudo gedit /boot/grub/menu.lst

type them in the terminal (Applications->Accessories->Terminal)

Also, do you get any errors while trying to boot into Windows?

---

