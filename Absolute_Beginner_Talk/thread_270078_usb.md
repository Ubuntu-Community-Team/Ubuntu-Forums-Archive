---
title: "usb"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by jocho on 2006-10-02
Could someone tell me another way to get in & out files an music from my Pendrive?...and how could i know the one that works right on linux?...the one that i have, seems to work fine at the beginin´;i used to put some music on it,but in order to get rid of them i had to erased it in windows(i couldn´t do it on ubuntu, at least i don´t know how!!!](*,) !!!...i´ve been very patience with ubuntu, but i know there´s a lot to learn. THANKS YOU GUYS OUT THERE!!!!!!:-D

---

### Post by arkangel on 2006-10-02
use System>>Gparted and format your pendrive as fat32  this way will be accesible by linux and windows 

when you erase one file a  hidden folder  is created it is .Trash so your files are  invisible and your pen drive seemsto be empty but actualy your pen drive is full

open your pen drive in the file manager and  press ctl+h  that will show  all files

---

### Post by PPAAUULL on 2006-10-02
Aren't USB keys usually formatted as FAT32 in the first place????

---

### Post by jocho on 2006-10-02
i DIN´T GET HOW TO DO THAT!!!....SEEMS TO BE EASY BUT ON SYSTEM I DON´T SEE ANY Gparted. I TRIED TO DO IT IN DISK&FILES....

---

### Post by PPAAUULL on 2006-10-02
You have to install gparted. it doesn't come installed basic.

---

### Post by jocho on 2006-10-02
Well...but how ppaauull?. how is the command

---

### Post by jaboua on 2006-10-02
1) Use the graphical installer, Synaptic
2) run "sudo aptitude install gparted"

It would also be possible to use the command mkfs.vfat to format the pen without any graphical partition editor, but be careful what drive you format however.

---

