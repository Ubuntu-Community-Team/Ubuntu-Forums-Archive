---
title: "settings for grub boot loader??"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-10-25
I have installed kubunutu 6.06 
in the grub boot loader I want that win xp shuld be the default
first boot choice.
and also i want to increase the countdown time from 10s to 30s

how do i do it

---

### Post by TitusDalwards on 2006-10-25
```
sudo nano /boot/grub/menu.lst
```

in that text file change timeout section 10s to 30s and for default  OS change default part for Windows Xp

---

### Post by jkvv_1973 on 2006-10-25
check this thread out

[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)


it will show you how to install "GrubEd" (case sensitive!!!!when installing)

its a gui to do all these things...very simple...make sure to follow instructions...:twisted:

---

