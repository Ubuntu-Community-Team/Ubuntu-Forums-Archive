---
title: "accesing other folders with some applications"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by airix on 2007-03-07
Hello all! 
I don't know how to acces other folders with any program, for ex. : menu--> file--> open --> (browse folder tree ) ... other that /home and /media   

for example I do this with k3b, and I can only acces /home and /media...

how can I make unhidden and accesible (at least readable) the rest of the folder tree??? or at least /mnt/windows_c etc? (which are mounted, accesible etc) 
I tried to open an image from /mnt/windows_c to burnit with k3b but I cannot see it from within the k3b... although is mounted and fine... 

how can I turn this off?

I used fedora, slackware and now I'm with ubuntu and I like it except this thing with the folders... idiot proof OS or what :confused: 
thank you and sorry for my english

bye bye

---

### Post by tkjacobsen on 2007-03-07
KDE uses a file named .hidden in the root folder (/). All files listed in here are invisible from KDE applications. You can just backup and edit/delete that file and the folders should be visible.

---

