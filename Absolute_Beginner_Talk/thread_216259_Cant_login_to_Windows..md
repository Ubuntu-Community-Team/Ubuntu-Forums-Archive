---
title: "Cant login to Windows."
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-15
Ok heres my problem. 
I just updated my system using the popup in the upper right corner telling you to do so. But way before, I decided to update, I had used this command in the console:

gksudo gedit /boot/grub/menu.lst

I did this, so I could make windows my default boot, and boot the timeout down to 5 secunds instead of 10. But after I upgraded my system, Windows doesent show up. So know I cant acces Windows. Whats wrong?

---

### Post by jincast90 on 2006-07-15
Nevermind. I got it working again. I remembered I had a backup off the document on my memorystick. Pfew :D

---

### Post by verbatim210 on 2006-07-15
LOL! never seen a problem fixed so fast
solved before finished reading the question

---

### Post by Malac on 2006-07-15
Just for information this happened to me too, I luckily had a backup that I could copy the Windows partition info from so I transfered that and all was well.
Before if I installed any new images GRUB re-scanned and re-found my Windows partition, now it only finds Ubuntu stuff.
I think this may be a bug in the upgraded GRUB, don't know if this should be filed as bug report or not.

---

### Post by verbatim210 on 2006-07-15
grub has never missed a windows installation in my experience
worse thing thats happened is it installs an additional entry on top of the existing entries leaving duplicate entries

---

### Post by T-Rexx on 2006-07-15
Same thing happened to me after I updated. Windows shows up in the GRUB menu at boot-up time, but GRUB won't let me select it (the highlight bar stays stuck on the first selection and can't be moved). After the ten second time-out, Ubuntu 6.06 (the default) boots.

Unfortunately, I hadn't saved a copy of my files. So I had to re-install Windows and then re-install Ubuntu. Same thing happened again after an upgrade of the kernal, however.

It appears the new GRUB doesn't support dual-booting. (So much for all that "GRand Universal" crap.........).

---

