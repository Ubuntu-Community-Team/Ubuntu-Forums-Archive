---
title: "black screen after boot"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by divindavid on 2008-03-09
hello so i just reinstalled ubuntu on my laptop (IBM T-22) and now after the loading screen i get a black screen. i have tryed ctrl alt f2 and it does it thing. then right after.....nothing :( . so thats all i can do with out of any of you guys help

---

### Post by ghost_ryder35 on 2008-03-09
can you boot into the Recovery Mode in the GRUB boot options

---

### Post by skymera on 2008-03-09
maybe you have the wrong graphics driver set up.

run

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

then follow the steps and restart.

if no luck try ```
 sudo dpkg-reconfigure xserver-xorg 
```
then choose the graphics driver manually.

---

### Post by divindavid on 2008-03-09
yes i can but what commands do i do??

---

### Post by divindavid on 2008-03-09
> **skymera said:**
> maybe you have the wrong graphics driver set up.

run

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

then follow the steps and restart.

if no luck try ```
 sudo dpkg-reconfigure xserver-xorg 
```
then choose the graphics driver manually.

now would i do that in recovery mode??????

---

### Post by ghost_ryder35 on 2008-03-09
> **divindavid said:**
> now would i do that in recovery mode??????
Yes :guitar:

---

### Post by divindavid on 2008-03-09
i tryed sudo dpkg-reconfigure xserver-xorg and it is asking me to find my video cards bus identifier what is that i have a laptop so it is buit in

---

### Post by divindavid on 2008-03-09
still does not work
after bolth commands

---

### Post by RequinB4 on 2008-03-09
If you read the paragraph introduction, many of the prompts it will give you can be left blank - this of course assumes that the OS recognizes your hardware.  If it does not work, try a "lspci" to find whether it is recognized and "lspci -v" for more information.  THis shouldn't be an issue, however, because you see the usplash.

Edit:  What is your moniter / video card

---

### Post by divindavid on 2008-03-09
for the seccond command Reauinb4 it says that every piece of hard ware is compatable

---

