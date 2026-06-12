---
title: "help with setting up desktop"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by GILBERTO15 on 2007-01-09
i just got done setting up the xubuntu alternative cd[[IMG]http://img77.imageshack.us/img77/8910/mvc007snx8.th.jpg[/IMG]]("[URL=http://img77.imageshack.us/my.php?image=mvc007snx8.jpg)"][[IMG]http://img77.imageshack.us/img77/8910/mvc007snx8.th.jpg[/IMG]](http://img77.imageshack.us/my.php?image=mvc007snx8.jpg)[/URL]
but i get this man sudo root thing, i just want to get to the desktop

---

### Post by tonyr1988 on 2007-01-09
What happens if you type

> startx

---

### Post by GILBERTO15 on 2007-01-09
here another picture befor i type startx[IMG][[IMG]http://img211.imageshack.us/img211/3495/mvc008scv2.th.jpg[/IMG]](http://img211.imageshack.us/my.php?image=mvc008scv2.jpg)[/IMG]

---

### Post by GILBERTO15 on 2007-01-09
now heres what happens when i typed startx[IMG][[IMG]http://img211.imageshack.us/img211/2661/mvc009snm6.th.jpg[/IMG]](http://img211.imageshack.us/my.php?image=mvc009snm6.jpg)[/IMG]

---

### Post by GILBERTO15 on 2007-01-09
heres another pic                               [IMG][[IMG]http://img243.imageshack.us/img243/954/mvc010sro9.th.jpg[/IMG]](http://img243.imageshack.us/my.php?image=mvc010sro9.jpg)[/IMG]

---

### Post by GILBERTO15 on 2007-01-09
what type of command do i have to type, i didnt install the server but i did install the xubuntu alternative cd, does it have the GUI?

---

### Post by GILBERTO15 on 2007-01-09
please help

---

### Post by Fireware on 2007-01-09
Here is what I did: 

**sudo aptitude update**

Then type after this command....

**sudo aptitude install xubuntu-desktop**

Make sure you have the CD in before though.

It will probably take about thirty minutes to install the XFCE desktop (Xubuntu's desktop).

---

### Post by floke on 2007-01-09
Does anything happen if you type:

sudo apt-get install xubuntu-desktop

(just a guess here, I recently put it on one of my machines from ubuntu - but the 'desktop' download pulls in everything you need, so if anything's missing this might solve it??)

or you could try...

sudo dpkg -reconfigure -phigh xserver-xorg

(actually I would try this first)

Hope it helps (though guessing it might not...)

---

### Post by GILBERTO15 on 2007-01-09
i did everything and know i get a screen with a cursor


[IMG][[IMG]http://img297.imageshack.us/img297/2001/mvc011swz4.th.jpg[/IMG]](http://img297.imageshack.us/my.php?image=mvc011swz4.jpg)[/IMG]

---

### Post by doobit on 2007-01-09
You need to configure X for your monitor and graphics card. What are your monitor and graphics card?

---

### Post by MkfIbK7a on 2007-01-09
try typing

xinit

---

### Post by GILBERTO15 on 2007-01-09
i installed it again and it shows ubuntu login? i thought i installed xubuntu, then it show command scripts, 
[[IMG]http://img175.imageshack.us/img175/6788/mvc013str8.th.jpg[/IMG]](http://img175.imageshack.us/my.php?image=mvc013str8.jpg)

---

### Post by GILBERTO15 on 2007-01-09
heres anotha pic 

[IMG][[IMG]http://img406.imageshack.us/img406/6124/mvc014syn0.th.jpg[/IMG]](http://img406.imageshack.us/my.php?image=mvc014syn0.jpg)[/IMG]

---

