---
title: "How do I get to the GUI from CL"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by BITstate on 2007-12-25
I installed ubuntu on the harddisk connected, I have put the harddrive back in my Laptop, booted up and get the CL, if I type "xstart" I get command not fould.

If I put harddrive in the PC again I get the ubuntu desktop.

Do I need to reconfig the GUI for use on the laptop?

The laptop is a HP omnibook 2100

---

### Post by walkerk on 2007-12-25
```
startx
```

---

### Post by tibellus on 2007-12-25
Actually, the command is ```
startx
``` which will take you to GNOME.

---

### Post by taurus on 2007-12-25
You need to reconfigure your X server again since you don't have the same graphic card and monitor.  Log in with your username and password.   Then at the prompt, run

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by BITstate on 2007-12-25
OK, GUI is working, but very slowly, maybe I enter some information incorrectly, so I will try to reconfig again.

Thank you for your help everybody.

You wouldn't get this sort of support on any day of the year from microsoft - It is Christmas Day and I have the full support of Linux users and my computer is working!

Who needs Microsoft!...

---

### Post by taurus on 2007-12-25
What graphic card do you have and have you installed any driver for it?

---

### Post by BITstate on 2007-12-25
I do not know how to find out which graphics driver is in this Laptop, I am a new user of Linux.
The Laptop is a HP omnibook 2100.
Do you know how to find out, and also how to install the correct driver?

---

### Post by fatality_uk on 2007-12-25
> **BITstate said:**
> I do not know how to find out which graphics driver is in this Laptop, I am a new user of Linux.
The Laptop is a HP omnibook 2100.
Do you know how to find out, and also how to install the correct driver?

From the command line type
```
lspci
```
In there will usually be a line "VGA compatible controller:" Post that line back here and will be able to find the right driver :)

Dobry wieczór BITstate.
Jak si&#281; masz?

Sorry my Polish is very limited :) as you can see!!

---

### Post by BITstate on 2007-12-26
OK 

VGA Compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)

Good Atempt with the Polish my friend, but I am English, I just live in Poland.

I am OK, thank you.:lolflag:

---

