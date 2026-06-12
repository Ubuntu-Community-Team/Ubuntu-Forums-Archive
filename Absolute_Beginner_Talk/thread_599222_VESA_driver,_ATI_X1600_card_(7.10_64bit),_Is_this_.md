---
title: "VESA driver, ATI X1600 card (7.10 64bit), Is this right?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by studo77 on 2007-11-01
I installed the 64bit 7.10 Gutsy, after running 7.04 for a while. I am quite happy with the upgrade, especially after i found a solution for installing 32bit firefox with Java.

To my wonderings.

I am using the standard restricted driver for ATI. System>Administration>Restricted Drivers Manager says that it is active and in use.

I have installed and am using compiz, with the built in gutsy. System>Settings>"Looks">Visual Effects set to Custom.

Everything seems to work just fine, got the cube, and other desktop effects working.

Only thing not working is Nexuiz, a known error, people have been getting this to work with the 8.42.3 drivers. But they are getting lousy scrolling in f.e. Firefox.
So this is a no-go.


Lots of people are going away from the VESA-driver, but why? I am new to Ubuntu, so explain please...


My system settings are (automated, i did not change anything... yet)
in xorg.conf:
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

In system>administration>screens and graphics>graphics card:
Vesa Generic for both screens, and screen 2 is disabled.


When i try to choose something else in
In system>administration>screens and graphics>graphics card
And press test, the screen goes gray and low-res.

I am not asking for a howto install the 8.42.3-driver, there is many. I am asking which settings are for optimal use with the delivered restricted drivers in 7.10 (64bit)?

---

### Post by damotor on 2007-11-01
VESA driver offers no 3d acceleration and the resolution sould be smaller than desired. 
if you look at your code
```
Section "device" #
Identifier "device1"
Boardname "VESA driver (generic)"
Busid "PCI:1:0:0"
Driver "fglrx"
Screen 0
EndSection
```
You are not using the VESA driver but the fglrx (the restricted modules), the VESA you see in your xorg.conf is related with the Boardname, s kind of second identifier (nothing important) but remember that the driver you are using comes from the Driver tag, wich is fglrx

---

### Post by Habo on 2007-11-01
hi, studo77

what are you getting if you type fglrxinfo in terminal?

Habo

---

### Post by studo77 on 2007-11-01
This is fglrxinfo output:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6473 (8.37.6)

So i should not be concerned about me seeing VESA all over the interface, and xorg.conf. A bit confusing... What if it gets messed up and named Soundblaster 16, then i still would have my 3d-desktop, but very confusing GUI.

also found this in my xorg.conf
Section "Extensions"
	Option		"Composite"	"0"
EndSection

In 7.04 this line stopped me from running compiz. It should be "1", but now it runs fine??? Sometimes this linux-thing is confusing. But i am getting there.

---

### Post by Habo on 2007-11-01
As I can see fglrx driver for your graphic card works fine.

fglrx driver from ATI Ver.  8.37.6 doesn't support composite, so, in Ubuntu 7.04 you cannot use compiz under AIGLX as standard  platform for accelerated indirect GLX rendering in Ubuntu. If you want to run it on Ubuntu 7.04 you need to install XGL that simulate composite. 
Since Ubuntu 7.10 for those user who have ATI cards XGL is made to be standard rendering platform. 
The newest driver from ATI - 8.42.3 suports composite and AIGLX, but you need to install it manually. It supports dual screen to so you will be able to configure and run 2 monitors with your graphic card.

---

### Post by studo77 on 2007-11-01
Habo: Thank you for an easy to understand explanation.
I never gave it much thought, i had enough going just to find out how to use Ubuntu.

And xgl as standard.... I still had to add xserver-xgl before compiz would run.

As for 8.42.3, still too soon. People having slowdown on the desktop (scrolling), varius installation methods (for a newbie, it looks like that, when seeing inst. instr.) and dual screen i have no need for right now.

---

