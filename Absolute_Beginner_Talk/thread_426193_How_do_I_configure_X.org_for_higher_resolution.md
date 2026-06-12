---
title: "How do I configure X.org for higher resolution?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-04-28
I have installed Xubuntu 7.04 but as usual with my old-age Matrix graphics card I only get a measly 800*640 resolution. [-(  I know I need to configure X.org but don't remember how to do it.  I remember last time I did it with some kind of app, but I don't remember its name.
I have neither xorgconfig nor xorgcfg and matroxset doesn't work. :confused: 
Hope you are wiser than me.  Thanks.

---

### Post by madmetal on 2007-04-28
open terminal and type
 sudo gedit /etc/X11/xorg.conf 
then modify the xorg.conf and save the changes..

something like this..
SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection

---

### Post by bapoumba on 2007-04-28
> **Blofeld said:**
> I have installed Xubuntu 7.04 but as usual with my old-age Matrix graphics card I only get a measly 800*640 resolution. [-(  I know I need to configure X.org but don't remember how to do it.  I remember last time I did it with some kind of app, but I don't remember its name.
I have neither xorgconfig nor xorgcfg and matroxset doesn't work. :confused: 
Hope you are wiser than me.  Thanks.

**sudo dpkg-reconfigure xserver-xorg** ?

---

### Post by Blofeld on 2007-04-28
@Mad:  Thanks for your suggestions.  By Jove, I didn't even have gedit installed!  But strangely, the entries for the higher resolutions are there and yet X.org won't use them!

---

### Post by ernierasta on 2007-04-28
:mad: There is a lot of howtos on the internet about xorg settings.

Before you ask use your brain a little and look at google.

I know I should not answer your question, but I will, I was (I am still) noob also. In terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
```
sudo gedit /etc/X11/xorg.conf
```
Now you see configuration of your x server. In 'Section "Screen"' you will see resolutions of your monitor. You can add anything you want, BUT REMEMBER (!) first entry is defaut. Here is example of mine config:
```
Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1280x960"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1280x960"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1280x960"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1280x960"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1280x960"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1280x960"	"1024x768"	"800x600"	"640x480" # in my case this row is the most important.
	EndSubSection
EndSection
```
 If you change or add resolution that your monitor or graphic card can not handle you will end with command line. If that happen login and write:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
reboot
```
It will be good you write down on the paper this last two rows. If something will go wrong you should be able to start from beginning.

EDIT:
Ok I am late. If you have not gedit, use what you have f.e. "nano". 
And don't forget to restart x server. ctrl - alt - backspace.

---

### Post by en3rgy on 2007-04-28
I need help with this too. My resolution is 800x600@50hz and my xorg.conf says 1024x768 (please see below). What am I doing wrong?

> ection "Monitor"
	Identifier	"Sony 17sf II"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeFORCE 6800 ULTRA"
	Monitor		"Sony 17sf II"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tyboon on 2007-04-28
Try this....open the terminal and type...

sudo dpkg-reconfigure -phigh xserver-xorg

It will prompt you to screen...then you peak the driver for your graphic card and then by pressin the "space" button you select wich resolution you like..
:guitar:

---

### Post by en3rgy on 2007-04-28
Voila! That worked! Thank you VERY VERY much! Now I can continue on my knowledge journey of Ubuntu.

---

### Post by Blofeld on 2007-04-28
@Bapoumba:  Merci, c'était pénible mais une réussite!

---

### Post by bapoumba on 2007-04-28
> **Blofeld said:**
> @Bapoumba:  Merci, c'était pénible mais une réussite!
Eh eh, félicitations :)

When going through reconfiguring xserver-xorg, keep the default answers when you do not know. When prompted to choose screen resolutions, select the ones wanted with <space> (place a * in the [   ] box) and restart X when done (CTRL-ALT-Backspace).

Enjoy!

edit: with xfce, you can use **mousepad** to edit files in a graphical session (with or wthout gksudo ;))

---

### Post by houstonbofh on 2007-04-28
To get a resolution, both the graphics card, and the monitor must support it.  And X must know this.  'sudo dpkg-reconfigure -phigh xserver-xorg' will allow you to change the settings for your card and monitor.

---

