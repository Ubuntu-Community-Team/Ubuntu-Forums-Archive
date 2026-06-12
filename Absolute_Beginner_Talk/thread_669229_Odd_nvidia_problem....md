---
title: "Odd nvidia problem..."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by censored77 on 2008-01-16
Bit of a cross-forum post, but no-one was able to help it seems. Apologies if this isn't the done thing!

I could never get Ubuntu 6 to work with my video card (geForce 5200) at anything other than 640 x 480, - it simply didn't give me the option for anything else, so I gave up.

Now I decided to give Ubuntu another go. I've installed 7.10 and it works fine with the open source drivers. However, if I switch to the restricted drivers to get all the visual wizzy stuff, it reverts to 640 x 480. Even if I set the Monitor to be a 1280 x 1024 LCD, and set the Screen Resolution to be 1280 x 1024.

All this does is to give me a much bigger desktop, complete with whizzy visuals, but displayed at low res and I have to scroll around it!

Any ideas?

---

### Post by KhaaL on 2008-01-16
Have you tried running nvidia-settings ? type that command in a console and try it out!

---

### Post by censored77 on 2008-01-16
No joy. I've set the settings for the screen and graphics to 1280 x 1024, but in nvidia-settings I only get the option to use 640 x 480 at most :confused:

---

### Post by SOULRiDER on 2008-01-16
Try this in a terminal to reconfigure xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by censored77 on 2008-01-16
xserver seems to be ok, I think.... :confused:

here's the relevant bit:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
```

But still all I get is 640x480 scrolling even if I set it to 1280 x 1024 in the menus too.

nvidia-settings still only gives the option of 640x480.

---

### Post by Digger78 on 2008-01-16
```
sudo apt-get xresprobe
```

```
sudo xresprobe nvidia
```

it should display something like

```
id: screen ID
res: 1024x768 800x600 720x400 640x480   [COLOR="Red"](these are the available resolutions, if the one you want is not there, you cant have it)[/COLOR]
freq: 30-61 56-75   [COLOR="Red"](HorizSync & VertRefresh If these are different in your xorg.conf try changing them)[/COLOR]
disptype:
```

---

### Post by censored77 on 2008-01-17
Will give that a go later. What if it doesn't work -  by "you can't have it" do you mean my system simply isn't capable of it?

What I don't understand is the open source drivers are fine. So why should the restricted drivers only do low res?

---

### Post by Digger78 on 2008-01-17
> **censored77 said:**
> Will give that a go later. What if it doesn't work -  **by "you can't have it" do you mean my system simply isn't capable of it?**

What I don't understand is the open source drivers are fine. So why should the restricted drivers only do low res?

Correct.

What make and model is your monitor?

---

### Post by censored77 on 2008-01-18
It's not a well-known make, DGM. It's capable of up to 1280 x 1024 and has no trouble in XP of in Ubuntu with the open source drivers.

Surely if the monitor wasn't able to do it, the driver would try and I'd just get a black screen and "out of range" message?

---

### Post by Digger78 on 2008-01-18
[B]can you post the output from post #6
[/B]
Are you using the latest nvidia driver installed via Envy?

---

### Post by censored77 on 2008-01-20
Ok well all I get is:

```
id: 
res: 800x600 640x480
freq: 
disptype: 
```

Which doesn't look too good...

---

### Post by Digger78 on 2008-01-20
try changing the  HorizSync & VertRefresh and personally i would remove or comment out  the modeline stuff

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	[B]Horizsync	30-80
	Vertrefresh	60-75[/B]
**#**  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
**#**  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
**#**  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
**#**  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
**#**  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
**#**  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
**#**	Gamma	1.0
EndSection
```

I dont know about 1280x1024 because my monitor is not capable of it, but i have the same card as you and i can without any problem get 1024x768

Heres MY monitor and screen sections

```
[COLOR="Red"]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        HorizSync  30-61
        VertRefresh  56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce FX 5200"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600"
	EndSubSection[/COLOR]
```

---

