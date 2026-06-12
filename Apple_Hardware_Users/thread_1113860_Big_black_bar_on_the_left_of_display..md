---
title: "Big black bar on the left of display."
date: 2009-04-02
forum: Apple Hardware Users
---

### Post by Kristofer Gustafsson on 2009-04-02
Hi all! I'm using a white intel imac 20 inch. It's the previous generation. It's using a ATI radeon. When i use the ati driver. Aticonfig --intiial .. I get a black bar on the left and the rest of the desktop is "virtual" the desktop moves with the mouse when i move to right or left. 

I'm using a samsung 24 inch T240HD. It's my main display because i have disconnected the internal display on my mac. This makes any display connected main display. It works fine with non ati drivers in ubuntu and also in OSX.

My resolution is 1920 x 1200. If anyone got a solution for this black (very annoying) bar. I would be happy. 

Tell me if you need me to post xorg.conf, it's pretty empty though.

---

### Post by cyberdork33 on 2009-04-02
yes, please post the xorg.conf. It should have something in it since you used aticonfig.

If the xorg radeon driver works (which I am pretty sure it does since it works on my iMac) why don't you just use it?

---

### Post by Kristofer Gustafsson on 2009-04-02
Well the radeon driver.. That is if i use aticonfig to enable it gives me the bar.. Aint at home right now tho. So i cant post the config.

---

### Post by cyberdork33 on 2009-04-02
> **Kristofer Gustafsson said:**
> Well the radeon driver.. That is if i use aticonfig to enable it gives me the bar.. Aint at home right now tho. So i cant post the config.
ok then you are confusing me with your terminology

the "radeon" driver is an open source driver that comes with xorg

the "fglrx" driver is ATI's driver that you can install.

There is also the "ati" driver which I don't think works for you...

have you tried the proprietary driver? You will have to enable this in System > Adminstration > Hardware Drivers

---

### Post by Kristofer Gustafsson on 2009-04-02
Sorry about the confusion. 

I did what you said, system > administration > hardware drivers and then enabled the driver. 

And well it works but i still get the bar at the left when i switch to resolution in System > Preferences > Screen resolution. I can use a lower resolution of course but then everything is virtual, still high res but mouse move display area at edges.. So i think it's some setting in the xorg.conf then. So here it is! 

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

I think it's looking very thin :P /etc/X11/xorg.conf right?

---

### Post by cyberdork33 on 2009-04-02
> **Kristofer Gustafsson said:**
> Sorry about the confusion. 

I did what you said, system > administration > hardware drivers and then enabled the driver. 

And well it works but i still get the bar at the left when i switch to resolution in System > Preferences > Screen resolution. I can use a lower resolution of course but then everything is virtual, still high res but mouse move display area at edges.. So i think it's some setting in the xorg.conf then. So here it is! 

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection
```I think it's looking very thin :P /etc/X11/xorg.conf right?
it sounds like you have a widescreen monitor, but you are not using widescreen resolutions. You can try to find the modelines for your monitor and put them in the xorg.conf. that might help.

the xorg.conf is mostly not needed anymore. The xserver detects things on the fly now and uses those values.

---

