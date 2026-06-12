---
title: "Ubuntu not starting up"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by z3r0-c0d3r on 2005-09-20
Well, Ubuntu starts-up, up to when the GDM is supposed to load. The list ends and then the screen jst goes blank and stays blank!!!
I didn't use Ubuntu for a while because my router was down and i only had windows drivers for my ADSL modem. So now i can't get into Ubuntu or Windows because when I unistalled SP2 i get the BSOD at start up!!
now i have no operating system!
I luckily found a live CD
can anyone help with the Ubuntu problem??
please!

---

### Post by lompolo on 2005-09-20
Try by holding Ctrl + Alt and pressing F1. Then you can log in with your username and password to virtual terminal then type:

cat /var/log/Xorg.o.log |less
check for errors and post errors here. Some advanced user will help.

By Ctrl + Alt + F7 you get back to graphical mode.

---

### Post by techroach on 2007-11-03
I also have the same problem. After the boot up process (ie, after the Ubuntu logo goes and after the whole lot of black and white code jargon ends), I'm supposed to see the login screen. But, it goes blank. Backlight is there but its all black.

I tried pressing everything on my keyboard. Just didn't work. Sometimes I think Linux has a got a long way to go till it gets anywhere near how reliable good old Windows is. It may be buggy and virus-bitten but it does always boot up anyway. Not that I'm a Windows fanboy, I'm really pissed off, thats all. 

Oh, and please help me man !! :(

---

### Post by getmeoutofhere on 2007-11-03
Is this on Gutsy?  On Gutsy, if I activate the drivers in the restricted driver option, I get a blank when I next boot up.  In fact, the monitor has been turned off.  So, one should perhaps be careful about activating the drivers!

---

