---
title: "Help!  Radeon 9250 ATI PCI CARD KEEPS CRASHING!"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by drakebarimore on 2007-05-31
Can anybody please help me get Ubuntu to work using my PCI Radeon ATI 256MB graphics card?  I can load up the ubuntu LIVE CD and get to the desktop, but I can't do much beyond that.  Like if I pull up a game like chess or something, the system crashes (well at least it kills the monitor display everything else seems to keep going like the fans leds etc).

I can see that there is a fix listed up above, but I don't understand what most of that means.  Is there any step by step guide to make these cards work so that absolue beginners can follow along?

This is a new PC build (obviously my first) and I really want to get everything working.  I don't have the money to keep putting out for new hardware, so it would really be great if I could get this card working.  I have a borrowed card that I must return which is a SLI nVidia card (PCI-E) and it works great without any problems, but I can't keep that card, and I'm out of money for components.

So, can anybody help me get this running right?

---

### Post by jbrown96 on 2007-06-01
This guide has instructions if the LiveCd won't boot, but they should work even if it does. Instead of using "nano" as the editor for the first step, use "gedit" it will be much easier. Every time the LiveCD is loaded this fix will have to be applied. 
Ubuntu sometimes has problems if you are switching graphics cards, so try to use the same one throughout the process.

> I've seen many people, including me, have had problems installing Ubuntu 7.04, due to the problem that xorg.conf is not set up correctly. Follow this guide if Ubuntu cannot start from live cd, because you get an error message about that your graphical interface (X server) could not be started.

The bug is well known, just look at this link: Linky and this one: Linky

You do not need internet connection when following this guide, because we will not download anything.

All credits goes to strumluff who got me on the Ubuntu track, and the guy who found the workaround in the second Linky.

Let's get started

After booting from the live cd, choose "no" to view the X details. You'll end up in the terminal. Press enter to log in and write:

Code:

sudo nano /etc/X11/xorg.conf

In the "Monitor" section add the following lines:

Code:

HorizSync                36-52
VertRefresh              36-60

It should look like this:

Code:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	36-52
	Vertrefresh	36-60
EndSection

Now go to the "Screen" section. Remove all other resolution than "640x480". So it will look like this:

Code:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"640x480"
	EndSubSection
EndSection

Click F2 to save and quit. Now write:

Code:

sudo killall gdm
sudo gdm

Ubuntu should now start. Install Ubuntu. When Ubuntu is installed go to terminal and write:

Code:

sudo apt-get update
sudo apt-get upgrade

Now go to System>Administration>Enable Restricted Drivers Manager. Check the unchecked graphic driver. Go back to the terminal and write:

Code:

sudo gedit /etc/X11/xorg.conf

Add your default resolution you removed earlier in the guide. If 1280x800 is your resolution it should look like this:

Code:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"    "640x480"
	EndSubSection
EndSection

Click on save and exit. Restart Ubuntu, and everything should be working perfect now.

If you want to install XGL/AIXGL and Beryl follow this Linky.

For XGL: Scroll down to ..Alternate method: Using closed source FGLRX drivers from ATI.. and follow the guide from there.

Hope this helps for everyone who had this problem!

Ub

Write back if you still have problems.

---

