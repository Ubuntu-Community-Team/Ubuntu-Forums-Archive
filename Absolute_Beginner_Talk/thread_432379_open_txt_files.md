---
title: "open txt files"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Sladi on 2007-05-03
I just reinstalled Feisty and now it asks me if I want to run or view txt files (or xorg.conf) every time I doubleclick on them in Nautilus. 

Why is that and how can I change it please?:confused:

---

### Post by starcraft.man on 2007-05-03
> **Sladi said:**
> I just reinstalled Feisty and now it asks me if I want to run or view txt files (or xorg.conf) every time I doubleclick on them in Nautilus. 

Why is that and how can I change it please?:confused:

Right click on the txt file, click properties. Go to open with tab, then choose the program you want to open it with everytime.

Have fun now, and if your editting the xorg, backup backup backup, can't say it enough.

---

### Post by nanotube on 2007-05-04
that just depends on the permissions. if the file has execute permissions, then it will ask you.
xorg.conf really doesn't need execute permissions, since it's just a conf file, so just chmod it to 644, and it will stop asking you if you want to run it. same goes for any other file (as long as you are sure that it is not a script that needs to be executable).

---

### Post by Sladi on 2007-05-04
Thank you very much! :mrgreen: 

Regards, 
Sladi

---

### Post by starcraft.man on 2007-05-04
> **Sladi said:**
> Thank you very much! :mrgreen: 

Regards, 
Sladi

Your welcome, have fun with ubuntu. Don't forget to put Resolved in the title, so others know :)

---

