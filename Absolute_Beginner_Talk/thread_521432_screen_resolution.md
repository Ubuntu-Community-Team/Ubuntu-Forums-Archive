---
title: "screen resolution"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-08-09
I am trying to get my screen resolution set the same as my XP resolution ( 768 x 1024). Have tried $/ "gksudo gedit/etc/X11/xorg.conf" (found this in a post reply), but when I hit enter the error message "gedit/X11/xorg.conf" does not exist.  How can I (or is it not possible to) change my screen resolution. I know VERY little about Linux, using the terminal, or Ubuntu. Appreciate ant help.

---

### Post by splintercellguy on 2007-08-09
Type sudo dpkg-reconfigure xserver-xorg and follow the prompts.

---

### Post by overdrank on 2007-08-09
> **skyjacker said:**
> I am trying to get my screen resolution set the same as my XP resolution ( 768 x 1024). Have tried $/ "gksudo gedit/etc/X11/xorg.conf" (found this in a post reply), but when I hit enter the error message "gedit/X11/xorg.conf" does not exist.  How can I (or is it not possible to) change my screen resolution. I know VERY little about Linux, using the terminal, or Ubuntu. Appreciate ant help.

Hi the command is 
```
gksudo gedit /etc/X11/xorg.conf
```
There must be a capital X and a space between the gedit and /etc

---

### Post by Rocket2DMn on 2007-08-09
You mistyped, you forgot the a space between gedit and /etc/X11/xorg.conf - however, manually editing the file doesn't tend to work very well.
Run the reconfiguration command splitercell suggested, using TAB to move around and SPACEBAR to select.  When you get to the resolutions place, you should choose your monitor's max resolution and everything less.  After the configuration is complete, save any open documents and restart the X-server (GUI) with CTRL+ALT+BACKSPACE.  After you login you should be able to get your correct resolution by going to System->Preferences->Screen Resolution.

---

### Post by skyjacker on 2007-08-09
> **Rocket2DMn said:**
> You mistyped, you forgot the a space between gedit and /etc/X11/xorg.conf - however, manually editing the file doesn't tend to work very well.
Run the reconfiguration command splitercell suggested, using TAB to move around and SPACEBAR to select.  When you get to the resolutions place, you should choose your monitor's max resolution and everything less.  After the configuration is complete, save any open documents and restart the X-server (GUI) with CTRL+ALT+BACKSPACE.  After you login you should be able to get your correct resolution by going to System->Preferences->Screen Resolution.

I tried this method and her is what's listed for my resolutions;
ection "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"eView 17f3"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection

also if I do a $/ gksudo gedit /etc/X11/xorg.conf, the first screen to appear asks for a driver and defaults to "vesa". Do i choose ok and go from there? Help

---

### Post by Rocket2DMn on 2007-08-09
If you're using an nvidia card (which it looks like you are), select the "nv" driver.  If for some strange reason that fails, then you can use the vesa driver.

---

### Post by skyjacker on 2007-08-09
I got into the terminal program and it ask me all these question sabout the keyboard, mouse, etc. I do not klnow how to answer these. Is there any way I can just change my screen res. (which 800 X 600).  Thanks for your help so far... I may not have enough experience with Linux to do this after all, but I sure like Ubuntu..

---

### Post by Rocket2DMn on 2007-08-09
If you read through, most of the questions are pretty self-explanatory.  You should be able to accept defaults on most of the options, like you probably just have a standard US 105 key keyboard.  Make some educated guesses, you probably don't have anything outside of defaults, just read to check.  
Manually editing the xorg.file for resolutions almost never works, so this is the best way.  Please ask other specific questions if you have them.

---

### Post by philinux on 2007-08-09
If your system was set up correctly just look at top of screen then select 

System > Preferences > Screen Resolution.

If there are no choices other than 800 x 600 then post back

---

### Post by skyjacker on 2007-08-09
The only two choices I have on the menu you gave is 640 - 480 or 800 - 600.
Appreciate you help.

---

### Post by philinux on 2007-08-09
Sounds like the install did not auto detect your graphics card etc.

you will have to open a terminal.

Applications > accessories > Terminal.

This gives you like a dos prompt.

then enter

sudo dpkg-reconfigure xserver-xorg

cut and paste this into the terminal window.

Most of the stuff in there you can just hit ok cos it detects your keyboard/mouse etc or if its a splash screen(info) you have to hit esc to return to the prompts when pressing ok dont work.

The important stuff is your graphics card use the up down keys to find your manufacture

Just read the stuff that comes up.

---

### Post by skyjacker on 2007-08-10
FINALLY got a new resolution to work... Thanks to all who helped. I love Ubuntu. Now I can give Mr. Gates the boot.

---

