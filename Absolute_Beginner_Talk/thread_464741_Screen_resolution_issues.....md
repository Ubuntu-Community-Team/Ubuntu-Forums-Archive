---
title: "Screen resolution issues...."
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by SirNintendo85 on 2007-06-05
Sorry, I'm sure this has been answered 100000 times, but I just downloaded this today after being sick of Vista.  The only issue I am running into is my screen resolution.  When I try to adjust it, the only options are 800x600 or 640x480.  My monitor is 1280 x 800.  I don't know if my video driver has anything to do with it, but it's a Via Chrome 9 HC IGP.  Everything is working great, watched some youtube vids and my sound is working, I'm just wanting to fix this nasty screen resolution.  And please, try to use terms that are as simple as possible.  Thanks in advance.

Shawn

---

### Post by dhruva023 on 2007-06-05
if you have intel card:

try to install this packag from synaptic."  915resolution "

and then reboot.

it will set your resolution.

---

### Post by SirNintendo85 on 2007-06-05
No it's a Via Chrome 9 HC IGP.  I think that's the video card, right?

---

### Post by Feba on 2007-06-05
sudo dpkg-reconfigure xserver-xorg

---

### Post by SirNintendo85 on 2007-06-05
> **Feba said:**
> sudo dpkg-reconfigure xserver-xorg


That brings me to a screen where it asks to identify my card, and then doesn't do anything after that.  I saw elsewhere to go there and you could tinker with the settings, but it didn't pop up for me.

---

### Post by Feba on 2007-06-05
Try system -> administration -> restricted drivers manager, make sure your card is enabled, and if you can't increase the resolution then try running it again.

You might not have selected the proper graphics card, though.

---

### Post by SirNintendo85 on 2007-06-05
:(There is only 1 thing under that, and I don't think it has anything to do with the screen settings.

---

### Post by SirNintendo85 on 2007-06-05
Still looking for some help....

---

### Post by Rocket2DMn on 2007-06-05
Late night is not the best time to seek help.
I'm on my way to bed, but if you need people to help you, you're gonna have to give more information.
Post as much as you can about your video card and monitor and include the relevant information from the xorg.conf file:
you can access that by opening a terminal from Applications->Accessories->Terminal and typing:
```
sudo gedit /etc/X11/xorg.conf
```
You can copy and paste in the whole file if need be, but if you can narrow it down to the video and monitor stuff, that would be best.
Good luck!

---

### Post by SirNintendo85 on 2007-06-05
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
EndSection

---

### Post by Feba on 2007-06-05
definitely looks to me that you need to run sudo dpkg-reconfigure xserver-xorg


What button are you pressing to try to select your graphics card?

---

### Post by SirNintendo85 on 2007-06-05
I chose VIA (even though when I pop it up it has Vesa there), then it asks me to type the name of the card so I do and press enter.  Then it brings me to a screen talking about Power PC machine users and what not, and I press enter and nothing happens and it just sits at this screen.

---

### Post by SirNintendo85 on 2007-06-05
> **SirNintendo85 said:**
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
EndSection



Anyone know what to do with these settings?  I'm trying to get 1280x800, since that is my default size on this computer.  I'm using a Via Chrome 9 HC IGP card on an EVEREX NC1501 laptop.  Everything is working excellent, such as sound, video, internet and what not, I just want to fix this screen issue.  I tried to mess with it last night, but ended up messing up my screen so bad that nothing was visible and had to reinstall Ubuntu.  Any help would be nice!!

---

### Post by SirNintendo85 on 2007-06-05
> **SirNintendo85 said:**
> Anyone know what to do with these settings?  I'm trying to get 1280x800, since that is my default size on this computer.  I'm using a Via Chrome 9 HC IGP card on an EVEREX NC1501 laptop.  Everything is working excellent, such as sound, video, internet and what not, I just want to fix this screen issue.  I tried to mess with it last night, but ended up messing up my screen so bad that nothing was visible and had to reinstall Ubuntu.  Any help would be nice!!
Please let me know if there are any other spec information things you need!  The only 2 options I am getting are 800x600 and 640x480, even after doing sudo dpkg-reconfigure xserver-xorg and putting in that I want 1280x800 settings.

---

