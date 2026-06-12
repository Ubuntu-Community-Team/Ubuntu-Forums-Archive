---
title: "Cannot start X Sever"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-09-08
After an upgrade from Kernel 2.6.20-15 to 2.6.20-16 and I now get a message when I boot via the -16 kernel "I cannot start the X sever (your graphical interface). It is likely that it is not set up crrectly. Would you like to view the X sever output to diagnose the problem?".
The system runs perfectly using the -15 kernel I even have Compiz working.

---

### Post by Crafty Kisses on 2007-09-08
> **avanrens said:**
> After an upgrade from Kernel 2.6.20-15 to 2.6.20-16 and I now get a message when I boot via the -16 kernel "I cannot start the X sever (your graphical interface). It is likely that it is not set up crrectly. Would you like to view the X sever output to diagnose the problem?".
The system runs perfectly using the -15 kernel I even have Compiz working.

You might want to try this command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by overdrank on 2007-09-08
> **avanrens said:**
> After an upgrade from Kernel 2.6.20-15 to 2.6.20-16 and I now get a message when I boot via the -16 kernel "I cannot start the X sever (your graphical interface). It is likely that it is not set up crrectly. Would you like to view the X sever output to diagnose the problem?".
The system runs perfectly using the -15 kernel I even have Compiz working.

Hi do you have a nvidia graphics card?

---

### Post by banewman on 2007-09-08
You need to set up the graphic card again - this is one area ubuntu has to work on in my opinion, updates wreck settings. 
Anyway, sudo dpkg-reconfigure xserver-xorg from the latest recovery kernel command prompt, choose the video card that best suits your system (if it isn't there choose "vesa" to get into the x display for the latest kernel) then reboot. :lolflag:

---

### Post by avanrens on 2007-09-08
NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce 8500 GT
	Card Type: PCI-E 16x
	Video RAM: 512 MB
	GPU Frequency: 490 MHz
	Driver version: NVIDIA UNIX x86 Kernel Module  100.14.09  Sat May 26 00:47:07 PDT 2007
I tried sudo dpkg-reconfigure xserver-xorg and type inthe video card info but it still didn't work.The above info obtained while running in kernel 2.6.20-15

---

### Post by avanrens on 2007-09-08
sudo dpkg-reconfigure xserver-xorg from the latest recovery kernel command prompt, choose the video card that best suits your system (if it isn't there choose "vesa" to get into the x display for the latest kernel) then reboot. 
Worked thank you.

---

### Post by overdrank on 2007-09-08
> **avanrens said:**
> NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce 8500 GT
	Card Type: PCI-E 16x
	Video RAM: 512 MB
	GPU Frequency: 490 MHz
	Driver version: NVIDIA UNIX x86 Kernel Module  100.14.09  Sat May 26 00:47:07 PDT 2007
I tried sudo dpkg-reconfigure xserver-xorg and type inthe video card info but it still didn't work.The above info obtained while running in kernel 2.6.20-15

How were the drivers installed on the 2.6.20-15 kernel?

---

### Post by avanrens on 2007-09-08
I used Envy to install the video drivers. After I got the -16 Kernel to work I had to re-install the video drivers again using Envy it all works perfectly now.
Thanks again.

---

### Post by overdrank on 2007-09-08
> **avanrens said:**
> I used Envy to install the video drivers. After I got the -16 Kernel to work I had to re-install the video drivers again using Envy it all works perfectly now.
Thanks again.

Great and good luck!

---

