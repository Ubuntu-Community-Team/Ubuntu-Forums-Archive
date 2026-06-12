---
title: "No resolution/hertz in xorg.conf"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-11-14
Hi

Last time I installed Ubuntu(Feisty) I had to manually edit /etc/X11/xorg.conf to get the right resolution and hertz.
I have now made a clean install with Ubuntu Gutsy, and now I dont understand xorg.conf longer, because it dos not mention resolution and hertz as it used to. And I also dont understand why «Identifier» is not the same; last time I remember it was very important that they where the same. Take a look here: 

```
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection
```

So, can I just add resolution and hertz? I need to know cus when I install the nvidia driver I get the wrong resolution and hertz and the GUI cant help me here.

And two non-important off topic question:
The program «Ubuntu Device Database» dosnt work, cant get past first check and it dosnt matter what I answer.
In Nautilus, the Emblemer are so smal they look more like dots, and there is no point to use them longer(cant see the symbol on them). Very sad, I really liked them in Feisty. 


Thanks for reading

---

### Post by philinux on 2007-11-14
Have a look in System>Prefs>screen resolution first.

---

### Post by sailor2001 on 2007-11-14
sudo dpkg-reconfigure -phich xserver-xorg

---

### Post by Inxsible on 2007-11-14
> **sailor2001 said:**
> sudo dpkg-reconfigure -phich xserver-xorgThat should be```
sudo dpkg-reconfigure -phigh xserver-xorg
``` But BEWARE, before you do this, make sure you make a backup copy. Also, once you do this, you will have to re-enable your graphics drivers and also other changes that you have made in your xorg.conf

you can make a backup by ```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf_backup
```

---

### Post by _sAm_ on 2007-11-15
Thanks for your answer:-) 

I did run the command that Inxsible provided; the only setting it would let me change was the resolution and nothing more. The xorg.conf now looks like this; 

```
Section "Monitor"

	Identifier	"Standard skjerm"

	Option		"DPMS"

	HorizSync	28-64

	VertRefresh	43-60

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"

	Monitor		"Standard skjerm"

	DefaultDepth	24

	SubSection "Display"

		Modes		"1280x1024"

	EndSubSection

EndSection
```

Still I wonder why &#8220;Identifier&#8221; is not the same on both section, since that was so important last time I changed this file(under Feisty). When I install the nvidia driver the nvidia-settings will report different hertz then the default screen settings in Ubuntu. Dont know if this is important.

The Scanning Frequency for my screen is (H, V) are 31 &#8211; 64 kHz, 59 &#8211; 61 Hz, so this is also not 100% correct in the file(my screen; [http://www.eizo.com/support/discontinued/lcd/s1910.asp](http://www.eizo.com/support/discontinued/lcd/s1910.asp)), but I dont know if its good enough.

When installing the nvidia driver and turning on compiz the window dialogs turnes light green when I resize them, should they do that?

---

