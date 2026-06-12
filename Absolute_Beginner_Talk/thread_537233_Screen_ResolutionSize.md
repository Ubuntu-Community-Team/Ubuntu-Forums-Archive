---
title: "Screen Resolution/Size"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by tom407 on 2007-08-28
Hi, I´m really new to linux, so sorry if this is some triviality, but after DLing ubuntu my screen size is now much smaller than it should be and centered on my screen with black around it. I have only two resolution choices 800x600 and 640x480. I originally had only one choice (640x480), but I followed a thread that did something to help. The reason I am having so much trouble with it is because I can´t see what I am typing with the command prompt (because of the small screen).

This is what I did to get the second screen resolution choice (couldn´t see what I was typing or any choices, just got lucky), pressed <ctrl>+<alt>+<F1> and entered the following code
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

and the thread said that if I am using KDE I should change GDM to KDM (don´t know what those are). 

Anyhow, I typed some of this code in and got lucky. While typing in I receive prompts for my password and such, but because I can´t see when this occurs I still think I have a prompt for the code, etc etc. Can anyone help me?

---

### Post by diatribe on 2007-08-28
what kind of video card do you have

---

### Post by johanvanzyl80 on 2007-08-29
I have the same problem. 
I just a got an HP Compaq 6910p notebook with a 14.1 widescreen. The display size is supposed to be 300 x 190 mm, but Gnome only uses a part of the monitor. It has two vertical black lines on both sides. I've played around with resolution in xorg, but only the 640x480 option works.
I found out that the native resolution for this notebook is 1280x800. The video card is an Intel GM965/PM965/GL960.
Does anyone have any idea?

Thanks
Joe

---

