---
title: "kubuntu 7.04 Live Cd"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by P01 on 2007-09-15
Hy,i have a little problem with kubuntu Live Cd.

Everything is work fine,Load desktop,icons,it runs perfectly,but mouse cursor is dissapear.I have a Microsoft Kit Keyboard + Mouse,and the samme problem is with Knopix Live Cd.
I want to try Kubuntu,becouse i like it for windows alternative.I don't like Vista SO,and i want to learn linux.Kubuntu is perfect for me,and i want to test this,first in LiveCd,and after i install on my computer.But this mouse cursor is drive me crazzy,i don't know what to do.\
Please help.
I'm windows user,but after microsoft release their Windows Vista,i changed my mind,about microsoft SO,i don't need the So can run verry slow,and you have to buy a super computer,only for special effect in Windows Vista.
So i start with Knopix,but after i see Kubuntu,=LOVe first seen.

My spec Is C2D E6600,X-FI Extreme GAmer,2x1GB DDR2 Kingmax,GF8800GTS,2X350GB SATA WD,Thermaltake SharkCAse,PSU550W Chieftec,Microsoft DM Edition Keyboard+Mouse.

Respect,

Ady :)

---

### Post by Daveth on 2007-09-15
I assume that this is a usb mouse? What happens if you unplug it, and then plug it back into a usb socket? 

Bear in mind that you are running in ram with the live cd, a completely different prospect from installing Kubuntu onto your hard drive.

---

### Post by P01 on 2007-09-15
Mouse is PS/2,not usb.
Thank's Daveth

---

### Post by P01 on 2007-09-15
Sorry for double post,i have instaled on my computer,and internet working,my printer working,all is working,but my cursor on my mouse dont work.i changed 4 models on mouse:2 on ps/2,2on usb,the samme problem.

---

### Post by Daveth on 2007-09-15
whilst this might be a kernel problem, it might be worth checking this post out:

[http://ubuntuforums.org/showthread.php?t=326225&highlight=bodzasfanta](http://ubuntuforums.org/showthread.php?t=326225&highlight=bodzasfanta)

to get into the xorg.conf file, in a terminal type

```
sudo nano /etc/X11/xorg.conf
```

If you are mouseless, hit alt F2, check "run in terminal", and have the above typed in the box,

and, being very careful not to delete anything accidentally, move down the file with the down arrow on the keyboard. Stop when you get to Section Input Device. Under the option part way down, check out what it says. My ps/2 mouse setting says "Protocol" "ImPS/2"

but you might what to explore the settings in the post above. Ctrl X, and agreeing to the changes with "y" will allow you to save the changes. If you only alter this you will not lose anything, but please be careful. Remember to close the terminal after, as you will be in superuser mode, and should not be.
It does seem that a number of folk are having similar sorts of problems. Hope that I have got all that down correctly!

---

### Post by Tecguy2 on 2007-09-15
wierd if it did the same with knoppix it must be a kernel issue or sumthing :confused:

---

