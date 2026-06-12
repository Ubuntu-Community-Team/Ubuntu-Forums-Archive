---
title: "Keyboard Acting Strange !!!!"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by RajivNair on 2007-07-15
hello everyone ,

           I dont know what has happened but all of a sudden .. since today morning my keyboard is acting a bit strange .. pressing "Tab" or "Caps Lock" .. takes me to the logoff window in GNOME and "Ctrl+T" key combination is not working ... i dont know if its a distro specific problem because i dont have any other OS ... can anyone help me solve this problem ...

thanks in advance ..
Rajiv Nair

---

### Post by starsky on 2007-07-15
hi there :)

do this 
```


$ sudo dpkg-reconfigure xserver-xorg


```
and select the right keyboard layout

HTH

---

### Post by DoricMan on 2007-07-15
I had this unusual problem the other day. My son was home and was using an identical Logitech mouse to me, the only problem he was in the next room next to to the separating wall. We both had a good laugh on this puzzling problem.
While on Wireless keyboards and mice. The other day, I had the keyboard  batteries go down and Ubuntu naturally became unusable. I had difficulty in closing Ubuntu and somehow managed to do so.
This leaves me with the following two questions.
Is there a way to find battery condition, for keyboard and mouse, in Ubuntu?
Lastly what is the best way of exiting Ubuntu with a non functioning  keyboard?
Post script. My thanks to all of you who have answered my previous problems, and I am now a very satisfied Ubuntu user.:KS

---

### Post by RajivNair on 2007-07-16
hi all ,

    well reconfiguring xserver dint help .. ive let my default layout to US and also im not using any wireless devices .. wht could be wrong .... plz help me solve this .. without "ctrl+t" .. working with firefox is so bad .. :(

thnx in advance ,
rajiv nair

---

### Post by expatCM on 2007-07-16
If you use the computer with a different keyboard, does the problem stay with the computer?

---

### Post by RajivNair on 2007-07-30
hi everyone ,

    got my issue resolved ... u were right "expatCM" ..the problem was with my keyboard

regards ,
rajiv nair

---

### Post by blumnday99 on 2008-05-15
I'm still having this problem.  I've tried using a different USB keyboard and it's still the same thing.  I'm getting an automatic shutdown whenever I use the numeric keypad on the right side of the keyboard.  This is really quite an annoying problem.

Anybody have any new ideas?  I've done everything in this thread already.

Mark

---

### Post by oninjao on 2008-05-15
uve mucked up ur keyboard config change to right one

---

### Post by blumnday99 on 2008-05-15
> **starsky said:**
> hi there :)

do this 
```


$ sudo dpkg-reconfigure xserver-xorg


```
and select the right keyboard layout

HTH

I've tried this and selected the us pc-101, pc-104, and pc-105 keyboards.  I've had the same problems with all the keyboards.  I didn't start having this problem until I upgraded to Hardy.

Mark

---

