---
title: "Blueberry iMac G3 wont load past ubuntu 6.10 cd splash scrn"
date: 2007-02-16
forum: Apple PPC Users
---

### Post by CowboyJTE on 2007-02-16
That's a pretty long title, hopefully it wont throw off the table...

I have a Slot-Loading Bluberry iMac g3, 400mhz, 128mb of ram. Yesterday I downloaded Ubuntu 6.10 for the PPC architecture from the imagepile mirror. Burned the ISO to a CD, and booted off of it. It boots and asks me what image I want to boot, so I tell it live, (with hopes to install later), it flashes white, then continues to the splash screen. (The Ubuntu Logo, the word, and then underneath a loading bar that bounces back and forth, then finally fills in from left to right). shortly after the loader bar is full, the splash screen disappears. It brings the system to a black screen, where you might expect to see a desktop, or an option menu. I can hear the CD being spun up and read, even though I cant see anything video wise.

Thankyou very much in advance. My boss just enlightened me with an email to a guide for editing the xorg.config, which I may try and dabble in, but I'll also be checking in here for responses. If I am able to edit that config file and everything works out I'll let you know.

---

### Post by cmeeks2662 on 2007-02-16
I think you will need more ram to run the live CD try an alternate installation CD

---

### Post by grazie on 2007-02-16
The incorrect config of the /etc/X11/xorg.conf file on G3 iMacs is a well known problem, so hopefully your email has the answers. If you get stuck with anything, post here. 

Also, as cmeeks2662 says, to do the install with only 128M of ram the alternate cd is needed, althouigh the desktop cd should still be usuable as a live cd.

---

### Post by fkdev on 2007-02-16
Note that, as mentioned, you may still need more ram (I think you're supposed to have 256 mb) but to fix the black 
screen, 
go to the terminal (from the 
black 
screen, by holding control-alt-f1) 
and:

```
sudo nano /etc/X11/xorg.conf
```

find your monitor section, and change it so it looks something like this (HorizSync and VertRefresh are important 
parts, the rest can be different):

```

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	60-60
	VertRefresh	75-117
EndSection

```

In addition, just to be safe, find your "Module" section, and comment out dri so it likes somewhat like this (dri for 
ppc r128 hasn't worked well since Hoary, and your computer probably has r128) :

```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	# Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

```


to restart X11: 
```
 sudo /etc/init.d/gdm restart 
```

---

### Post by linear on 2007-02-16
If memory serves, the "gdm restart" command is broken in Dapper and Edgy.

Try this instead: **sudo killall -HUP gdm**

---

### Post by grazie on 2007-02-16
/etc/inii.d/gdm restart is broken yes. I nearly always use ctrl+alt+backspace.

---

### Post by bodycoach2 on 2007-02-16
For that machine, I'd suggest Xubuntu 6.06.1

I've been unable to get any version of 6.10 to load on these older iMacs. 

I highly suggest downloading Xubuntu 6.06.1 Alternate Install CD. The LiveCD version seems to have problems too. Make sure you burn it VERY slow.

> **CowboyJTE said:**
> That's a pretty long title, hopefully it wont throw off the table...

I have a Slot-Loading Bluberry iMac g3, 400mhz, 128mb of ram. Yesterday I downloaded Ubuntu 6.10 for the PPC architecture from the imagepile mirror. Burned the ISO to a CD, and booted off of it. It boots and asks me what image I want to boot, so I tell it live, (with hopes to install later), it flashes white, then continues to the splash screen. (The Ubuntu Logo, the word, and then underneath a loading bar that bounces back and forth, then finally fills in from left to right). shortly after the loader bar is full, the splash screen disappears. It brings the system to a black screen, where you might expect to see a desktop, or an option menu. I can hear the CD being spun up and read, even though I cant see anything video wise.

Thankyou very much in advance. My boss just enlightened me with an email to a guide for editing the xorg.config, which I may try and dabble in, but I'll also be checking in here for responses. If I am able to edit that config file and everything works out I'll let you know.

---

