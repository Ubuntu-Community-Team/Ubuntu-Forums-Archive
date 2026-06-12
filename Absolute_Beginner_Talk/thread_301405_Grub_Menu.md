---
title: "Grub Menu"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Desy on 2006-11-17
Can someone please help me with my grub menu.  When i get the option to boot either ubunto or win xp i cannot highlight anything other that ubunto.  My keyboard works ok

---

### Post by Gaweph on 2006-11-17
cannot highlight? i do not understand.

Are you opening the menu.lst file with root (this is needed in order to edit it)

Just do:

sudo gedit /boot/grub/menu.lst before editing

---

### Post by ciscosurfer on 2006-11-17
Please use the search function on the forums here to search for issues relating to GRUB.  There are many threads that can help you out! :D

---

### Post by Desy on 2006-11-17
Sorry dont think i made myself clear.  I have 2 drives 1 with xp and 1 with ubunto.  When my pc buts up it gives me an option which os to boot to.  Ubunto is highlighted but I cannot use my arrow keys to highlight xp.  My keyboard works ok.  Hope this is more clear

---

### Post by Tomosaur on 2006-11-17
Is your keyboard USB or PS/2, or something different? Some older computers don't support USB during boot-up. Are you able to access the BIOS using your keyboard (by pressing the Setup key during boot, you should be able to see which key to press for several seconds, normally F2 or Del). If not, I would hazard a guess that yours is one such computer. If you have an older keyboard lying around (PS/2 or otherwise, just not USB), I would test that and see if it works.

---

### Post by Spookster on 2006-11-17
Also, assuming it's a USB keyboard, connecting it to the PC directly rather than through a hub often helps.

---

### Post by Gaweph on 2006-11-17
If it is a case of keyboard not active during boot, then im afraid there really isnt a fix, other than a new bios or a PS/2 keyboard (that will work on bootup)

---

### Post by Desy on 2006-11-17
Yes my keyboard is a usb connected to the pc and i can get into bios and do everything a keyboard is suppose to do except select  a different os

---

### Post by manishk on 2006-11-17
This happens with me also...but sometimes, not always.

I use a laptop and sometimes the keyboard gets 'locked' when the GRUB menu shows up and I cant do anything but wait for the timer to expire and load the default OS. Once in Ubuntu, the keyboard works again. 

Restarting helps. Try this: Press any key a couple of times just as the comp starts running...its notthing tech but it works for me!

---

