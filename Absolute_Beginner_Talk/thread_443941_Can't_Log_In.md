---
title: "Can't Log In?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by gsruizvtec on 2007-05-14
Ok I was having troubles with the cd burn and the install from windows stuff so I used that wubi netboot proggy.  My problem is everything is good but when I got to log in and password it doesnt go anywhere it just has my username@name thing where I can put in some sort of commands.  Im not completely incompetent I've come this far but I dont even see an ubuntu splash screen or anything just black with white type.  Any help plz?

Dan

---

### Post by bobplano on 2007-05-14
it sounds like your X isn't started. try sudo startx or sudo X or sudo /etc/init.d/gdm restart. does it come up with any errors about X?

---

### Post by gsruizvtec on 2007-05-14
Ok I tried that sudo startx and it said x wasnt installed.  So it said to install x type apt get install x or something similar to that after I did all that I tried it again and it aborted or something.  I just want to see a pretty splash screen and log in similar to this darn windows lol.  Thanks with the quick replies been workin on this for a few hours now.

Dan

---

### Post by gsruizvtec on 2007-05-14
When I log in it says ubuntu generic kernal something or other.  I log into that when it has my name login I but the username and password then im stuck at a command promp and cant go any further still hope that helps to solve my problem.

Dan

---

### Post by bobplano on 2007-05-15
X is the graphical interface so you need to specify which GUI you want. for example
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```
if you want you can just change ubuntu to xubuntu or kubuntu to get xfce or kde respectively

---

