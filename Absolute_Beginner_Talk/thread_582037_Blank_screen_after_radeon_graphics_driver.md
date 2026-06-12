---
title: "Blank screen after radeon graphics driver"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by -Theanimal- on 2007-10-19
I tried to install the ATI drivers from the resticted drivers menu(or something like that, forgot how it's called:P)and it all went fine etc.
I reboot and after the loading bar i have a blank screen and it does absolutely nothing:confused:
So i looked in the recovery mode, but i have no idea how i can fix something like this.

Can anyone help me with this?O:)

---

### Post by Pumalite on 2007-10-19
Note: This guide is based upon Ubuntu 7.04, so commands like "gedit" and "gdm" will not work with Kubuntu/Xubuntu/Edubuntu. Like, in Kubuntu "gdm" is "kde" and so on.

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

---

### Post by -Theanimal- on 2007-10-19
Thanks for the guide:)
but is there also a way trough the recovery mode?I would like to know more of the linux terminal etc.;)
If there isn't any way to do this with the recovery mode, i'll do what you said Pumalite

---

### Post by Bliepo32 on 2007-10-19
Everything he just posted works in the terminal, so t works in recovery mode. If you want to learn more about the terminal, you could try [http://www.linuxcommand.org](http://www.linuxcommand.org)

---

