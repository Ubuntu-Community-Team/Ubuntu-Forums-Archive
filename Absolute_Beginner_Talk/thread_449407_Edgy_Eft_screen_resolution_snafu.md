---
title: "Edgy Eft screen resolution snafu"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by smoaky on 2007-05-20
Hi
I recently switched back to 6.10 because the kernals used in Feisty caused my mouse to freeze up continually.
Now I am running Edgy and so far no mouse freeze-ups yet [-o<
However my screen resolution cannot be changed. When I try to set it to 1024x768 the screen goes black and it re-sets to the log-on screen again without changing the resolution.
And when you use the scroll wheel on the mouse the screen does not advance quickly up or down it looks like the page "waves" or "rolls"
Kinda aggravating :(
Any solution? be detailed step-by-step in your answer. remember I'm still very new to Linux and Ubuntu.;)
Thank you so much :D
smoaky

---

### Post by Kobalt on 2007-05-20
The solution to your problem is installing the drivers for you graphic card : which one is yours ?

---

### Post by smoaky on 2007-05-20
NVIDIA GeForce 6150. and BTW my mouse STILL freezes up. #$$#@!%^**^&^%%@#!!!

---

### Post by Kobalt on 2007-05-20
All right, one thing at a time. Go to System > Admin. > Restricted drivers manager. Activate the drivers for your video card from there and reboot. That should do it for your resolution thing.
About your mouse : what kind of mouse is it ?

---

### Post by smoaky on 2007-05-20
Uh...Im using Edgy Eft 6.10 There is no Restricted drivers manager under System> Admin.
I would have tried that like I did with Feisty,
I have a wireless USB mouse Logitech. I have tried switching to a wired mouse,no luck.
My mouse is directly plugged into the PC no USB hub being used. Tried using another port. Still freezes.

---

### Post by Kobalt on 2007-05-20
Dumb me! 
To install the drivers run the following command lines then : 
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```
And reboot. That should do it.

---

### Post by smoaky on 2007-05-20
Thank you I will try that within an hour or so. I am downloading open SUSE currently just in case I have to give up on Ubuntu. 
Can't stand KDE I neeed to have a distro using Gnome.This mouse freeze up thing is extremely aggrivating
Any suggestions ?

---

### Post by smoaky on 2007-05-20
BTW I am running a AMD Athlon 64 X2 4200  Dual Core CPU.
Should I be using the 64 bit version of Ubuntu instead of the x86 architecture?
I am running Ubuntu on an  USB external HDD with my PC running a dual boot of XP and Vista

---

