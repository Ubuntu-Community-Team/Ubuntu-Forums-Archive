---
title: "Graphics Problems"
date: 2007-06-25
forum: Apple Intel Users
---

### Post by alecfeld on 2007-06-25
For the past couple of months, I've had trouble installing Ubuntu. When loading up the desktop, I get some weird, distorted, slanted graphics which I have no idea how to fix. Therefor, I cannot install nor run from the live desktop. When installing with the alt CD, I get the same issue after installation. I'm on a 17" MacBook Pro. Any help?

---

### Post by Super TWiT on 2007-06-25
Usually this happens when the system is first starting the graphical interface of Ubuntu, however when this happened to me it lasted less then a second.  After that, everything was normal.  When it happened I was on a PC though.

---

### Post by cyberdork33 on 2007-06-25
drop to a console and edit the xorg.conf to use the vesa driver then you can restart and it should work. You can update and try to figure out the correct driver to use after that. This used to happen on iMacs in edgy too.

---

### Post by alecfeld on 2007-06-25
Sorry for sounding like such a noob, but how do I go to the console? I used to know this, but totally forgot.

---

### Post by cyberdork33 on 2007-06-25
Um.. On a standard PC keyboard it is CTRL+ALT+F1 (or F2, F3, etc) I am not sure if you use alt or command on an apple keyboard.

---

### Post by ronocdh on 2007-06-25
> **cyberdork33 said:**
> Um.. On a standard PC keyboard it is CTRL+ALT+F1 (or F2, F3, etc) I am not sure if you use alt or command on an apple keyboard.
Ctrl+alt+F-keys is correct on an Apple keyboard. Alecfeld, have you installed the fglrx driver? Also, if you consider yourself a noob, perhaps the command **sudo dpkg-reconfigure -phigh xserver-xorg** will treat you better than editing your xorg.conf by hand. Just a thought.

---

### Post by cyberdork33 on 2007-06-25
> **ronocdh said:**
> Ctrl+alt+F-keys is correct on an Apple keyboard. Alecfeld, have you installed the fglrx driver? Also, if you consider yourself a noob, perhaps the command **sudo dpkg-reconfigure -phigh xserver-xorg** will treat you better than editing your xorg.conf by hand. Just a thought.

I don't think he has gotten to a point where he has a system to use let alone downloaded drivers. The vesa driver will get X to start (visibly) and then you can install whatever other drivers you need after that.

---

### Post by ronocdh on 2007-06-25
> **cyberdork33 said:**
> I don't think he has gotten to a point where he has a system to use let alone downloaded drivers. The vesa driver will get X to start (visibly) and then you can install whatever other drivers you need after that.
Yup, you're right. :oops: Alecfeld, try the link in my sig about X failure? If you've a 17" MBP with an ATI card, it should help you out. I think you do, because you said "for the past couple months..."

---

### Post by alecfeld on 2007-06-25
I'll try it out, thanks :)

---

