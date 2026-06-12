---
title: "Reconfigure hdd question.."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-01-04
I have XP and 6.10 installed on the same hdd in that order.
If I remove XP with gparted, do I need to reinstall 6.10 to the front of the hdd or will there be  a usable partition ahead of 6.10?
I know I didn't say that very well, but I just want to get rid of XP altogether and leave the whole hdd for 6.10 without having to reinstall if possible.
Also is this the best method?
Thanks for any help.

---

### Post by jvc26 on 2007-01-04
I think you can just delete the XP partition and resize the Ubuntu one to take up the rest of the space.
Il

---

### Post by kidders on 2007-01-04
Yep :-) Almost nothing requires you to reinstall Linux. Resizing partitions is always slightly risky though ... I would just create a second one, all things being equal.

---

### Post by Bachstelze on 2007-01-04
No, you can't move the start sector of a partition without risking to put yourself into trouble. But just createing another partitin instead of the old XP one is no problem. GRUB doesn't care where the partition is when it boots it :)

---

### Post by Milt888 on 2007-01-04
So I should just reformat the whole hdd and reinstall 6.10 on it to be safe?
It really wouldn't be a problem. I just thought I might get around it.

---

### Post by kidders on 2007-01-04
Reformat your hard disk?! :confused:

Just boot your PC, replace your WinXP filesystem with a blank one, and you're done. Reinstalling your entire operating system seems like an awful lot of trouble to go to without a good reason.

---

### Post by jvc26 on 2007-01-04
If it wouldnt be a problem then thats the simplest thing to do as then you have your entire HDD all sorted out with Ubuntu from the start, but I dont think you HAVE to.
Il

---

### Post by Milt888 on 2007-01-04
Well I'll just format the thing and reinstall.
I'm so new to this I'd screw it up for sure trying anything else.
Thanks much for the advice.

---

