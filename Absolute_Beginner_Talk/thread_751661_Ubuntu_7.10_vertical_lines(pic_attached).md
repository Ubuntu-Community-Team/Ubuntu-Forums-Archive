---
title: "Ubuntu 7.10 vertical lines(pic attached)"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by UncleJoey on 2008-04-10
Hey all, new to Ubuntu so this forum is my new bible. 

I got together a cheap net PC and loaded 7.10 and theres a screen issue...or video driver issue. So I tried XP and no issues. I check the disc and loaded it on PC #2 and everything went perfect. 

[IMG]http://i257.photobucket.com/albums/hh223/joeslow/S5030429.jpg[/IMG]
Thats what I am looking at, and here are the specs:
*ECS Motherboard with on board video seen here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813135060](http://www.newegg.com/Product/Product.aspx?Item=N82E16813135060)
*AMD Sempron 3000
*512MB DDR ram
*40GB HDD

The visual issue occurred while on the live CD and after being loaded. I did what I could with adjusting the screen resolution and refresh rate. Its a 1280x1024 LCD monitor, even in other sizes it has a static to it.

---

### Post by overdrank on 2008-04-10
Hi and welcome, the link does not specify the graphics chipset so please use the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware, look for VGA and this will be your graphics.

---

### Post by UncleJoey on 2008-04-10
Thank you very much! Ok, I did what you said and heres what I have found out...

"01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 01)"

Does that help me find an adapter? I don't have a means of putting it on the net right now.

---

### Post by overdrank on 2008-04-10
> **UncleJoey said:**
> Thank you very much! Ok, I did what you said and heres what I have found out...

"01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 01)"

Does that help me find an adapter? I don't have a means of putting it on the net right now.

Ok I have not had much luck with the SIS graphics but there has been one thing that has helped others. In your xorg you can edit the default depth from 24 to 16 and it may help. No you do have Ubuntu installed before you try this.
Edit your xorg with this command ```
gksudo gedit /etc/X11/xorg.conf
``` Then you will find
Example
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
And you can try and change the 24 to 16 and save and exit. Then restart x with the key ctrl, alt, backspace bar. Hope this helps and good luck!

---

### Post by UncleJoey on 2008-04-10
I'm sorry but I really don't understand what I am supposed to do with that prompt. I put it into the terminal and gedit opened up. 

I guess I'll try ubuntu 6.06, i tried all of the drivers 7.10 had for the SiS video and its still having issues.

---

### Post by Tyke91 on 2008-04-10
I would suggest following the xorg.conf advice. the command he gave you is supposed to open up gedit and allow you to edit your xorg.conf file (the configurations file for Xserver, the base of your graphical user interface)

edit that one line from 24 to 16, save, and restart. see if it helps.

---

### Post by UncleJoey on 2008-04-10
Thanks. I am doing this, but it only brings up a blank window ...see in picture

[IMG]http://i257.photobucket.com/albums/hh223/joeslow/S5030426.jpg[/IMG]

---

### Post by UncleJoey on 2008-04-10
does it look like I am entering the code correctly?

---

### Post by smartboyathome on 2008-04-10
You aren't, you put tec, instead of etc.

---

### Post by kevin11951 on 2008-04-11
> **UncleJoey said:**
> does it look like I am entering the code correctly?

the origional advice was wrong. try:

```
gksudo gedit /etc/X11/xorg.conf
```

Then you will find
Example
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
And you can try and change the 24 to 16 and save and exit. Then restart x with the key ctrl, alt, backspace bar. Hope this helps and good luck!

---

### Post by UncleJoey on 2008-04-11
THANKS SO MUCH!!!

Got it fixed, not a single bug. Now to find a wifi solution tomorrow. 


Man, happy Ubuntu 7.10 guy here. 


code needed was "gksudo gedit /etc/X11/xorg.conf"

For you other newbs, go to Applications, Accessories, Terminal. Then post the above code in the terminal, it will open a window(after you enter your authorization psswd) and you can fin the color depth to resolve from 24 to 16. This fixed mine and so far so good.

---

### Post by overdrank on 2008-04-11
> **UncleJoey said:**
> THANKS SO MUCH!!!

Got it fixed, not a single bug. Now to find a wifi solution tomorrow. 


Man, happy Ubuntu 7.10 guy here. 


code needed was "gksudo gedit /etc/X11/xorg.conf"

For you other newbs, go to Applications, Accessories, Terminal. Then post the above code in the terminal, it will open a window(after you enter your authorization psswd) and you can fin the color depth to resolve from 24 to 16. This fixed mine and so far so good.

Hi and I do apologizes for the typo in the command. Good luck!

---

