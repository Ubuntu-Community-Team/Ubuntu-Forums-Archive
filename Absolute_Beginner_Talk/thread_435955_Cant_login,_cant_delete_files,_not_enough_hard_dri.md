---
title: "Cant login, cant delete files, not enough hard drive space?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Atow on 2007-05-07
ok i installed the latest xubuntu 64-bit on my laptop presario v5000 and it dual boots fine with winderz. i was transferring some stuff and it said my partition was full, i forgot i was transferring some stuff for video class and that filled it up fast. i went to delete it and i recieved an error msg stating that i didt have enough room to copy the files to the trash can......... i tried deleting other stuff and same error. now i had to go to class so i turned it off to figure it out later and then when i came back i cant login because there is not enough space to create a temp file..... help?

---

### Post by fakie_flip on 2007-05-07
Boot into single user mode and use the rm command to delete the files. To do that, choose recovery mode from the grub menu. If that doesn't work, you may try booting a live cd, mounting the partitions, and then deleting the files. You could also try shift+delete which skips the trash bin and deletes the files immediately.

---

### Post by Atow on 2007-05-07
thanks i'll try that now

---

### Post by fakie_flip on 2007-05-07
Okay, let me know if that works.

---

### Post by taurus on 2007-05-07
From a recovery mode, 
```
aptitude clean
```

---

### Post by Atow on 2007-05-07
yeah the RM commands worked just great. i just cd to where the vids were stored and deleted a few and i could login again. now i just have to get my wireless and sound to work >_< . thanks for the help on this one though

---

