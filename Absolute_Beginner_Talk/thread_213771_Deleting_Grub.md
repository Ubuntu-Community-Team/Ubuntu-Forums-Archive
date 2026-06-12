---
title: "Deleting Grub"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-07-11
I installed Ubuntu a few weeks ago on my XP machine.  I'm loving Ubuntu, but I just don't have enough drive space on this old computer to make everything work fine.  I need to fix the MBR to only install in windows, does that mean deleting GRUB or just changing the default to Windows?  And how do I do either?  Also, how can I repartition the hard drive? Thanks for all your help.

---

### Post by Drakkor on 2006-07-11
Boot with XP disk,select R for repair,then type fixmbr
This will eliminate grub and write a new master boot record
then right click my computer> disk management and delete the linux partition

---

### Post by scxtt on 2006-07-11
if you're just putting XP back on (no linux) booting w/ the XP disk in the CDROM will take care of everything ... if you're just removing linux, no XP reinstall, Drakkor is right-on-the-$$ ...

---

### Post by Drakkor on 2006-07-11
Correct, scxtt I was assuming it was dual boot :(  but Ubuntu  rocks ! 
Maybe try again with more disk space.

---

