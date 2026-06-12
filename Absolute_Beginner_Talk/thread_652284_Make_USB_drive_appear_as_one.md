---
title: "Make USB drive appear as one"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-12-28
i have an Integral Ice 2GB USB flsah drive.

When running WinXP it appears as TWO drives.

one is 2MB and holds a program
the pother is 2GB and has my music on.

in windows i enter my password in the program which in turn allows me to acccess the other 'drive'

in Xubuntu only the 2MB drive appears.

i need to make the whole thing appear as one so i can get my music and collegfe work off.

sorry if poorly expalined, its hard to :)

Thanks

---

### Post by tech9 on 2007-12-28
could you post your output of

```
fdisk -l
```

while your removable drive is plugged in?

---

### Post by psusi on 2007-12-28
Repartition/format the disk so that it does not use encryption.  Use gparted in linux or the disk administration applet in windows.

---

### Post by Mad_Dawg on 2007-12-28
Is your flash drive one of those with the U3 software on it?

What are you seeing in your Ubuntu?  I am assuming that you are trying to load the files into Ubuntu.

---

### Post by skymera on 2007-12-28
U3, hmm not sure

its a: Integral ICE 2GB USB 2.0 FlashDrive

a format is no use as i need the passwordto protect my collegework.

in ubuntu wheni plug it in all i get is my 2MB 'drive' pop up, thst has the .EXE in it.

Thanks

---

