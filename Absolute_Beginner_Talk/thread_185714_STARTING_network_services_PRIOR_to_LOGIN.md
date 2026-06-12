---
title: "STARTING network services PRIOR to LOGIN"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-06-01
[FONT="Times New Roman"][SIZE="5"]hi gang 

would anyone here know how to start networking services prior to logging in??? i'm thinking about having a samba file server but i noticed i had to log in before any other host can connect to the ubuntu... 

thanks in advance[/SIZE][/FONT]

sorry for the big font. wanted to keep it exciting! :D

---

### Post by bongobonga on 2006-06-01
Most network services are by default started before login.  The order in which they are started is controlled by the numbering of the scripts in the directory 
> 
/etc/rc2.d

The most lightly source of your problem is that either samba is not being started properly at boot time, or that it is not properly configured. 
First check that there is a link in that directory called something like "S20Samba". The number in the name of the link may be different on your computer.

---

### Post by ProjectGod on 2006-06-01
interesting! thanks for the reply...

you see i've got an ubuntu on an old machine that is without a monitor... i have recently installed xfce as people on this forum recommended me to do... i've also installed the "enlightenment" window manager... i want to check theses out! (as well as have a samba server)... i noticed that when i had a monitor it allowed me to change the session so i can choose which window manager to use... however VNC doesnt work prior to login... 

:mrgreen:

i'll try it out as soon as i get home :D

---

### Post by ProjectGod on 2006-06-02
yup s20samba is in the directory... :D

whatdo i do now?

---

