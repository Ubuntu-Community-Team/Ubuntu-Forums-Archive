---
title: "Temp and performace question"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by james.gravley on 2007-06-12
Ok this thread is kind of two questions in one

I have a Sony Vaio VGN-FS790 (Pentium M 2 ghz) that is about a year old. My temp. monitor posts CONSTANT temps of at least 75 C and without an ice pack on full CPU usage it can easily reach 98 CONSTANT. Now everything I have read  says that these temps will fry a processor, but mine is not fried and continues to work fine. I am missiing something?

Also, I have a friend (who actually introduced me to Ubuntu) that has a 3 yr old dell that can run Beryl like pro, whereas when I run Beryl I get black windows and my comp will barely run. I think for sure I am missing something here? (I have all updated drivers)

Any help or general comments would be much appreciated.

---

### Post by CrispyFried on 2007-06-12
the pentium m is rated for 100C but man running 98C is living on the edge. but temp sensors arent 100% accurate either. perhaps yours is off?


the celeron m in my notebook runs at 75 C pretty much constantly and its 3 years old. gets to 80C once in a while but I have to beat on it to do so.

---

### Post by starcraft.man on 2007-06-12
Ok, I don't know about your first question. It is concerning that it runs so hot, you may want to invest in a better cooling solution.

I do know about the Beryl question. Do you have an Nvidia card? If so, I have the solution follow my steps please:

1) Open any terminal and type in 

```
gksudo gedit /etc/X11/xorg.conf
```

2) Scroll down to the two sections I paste in the following, yours may differ just be sure to paste what I highlight in red in the same spot.

```
Section "Device"
	Identifier	"nVidia Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	[COLOR="Red"]Option          "TripleBuffer" "true"[/COLOR]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV40 [GeForce 6800 GT]"
	Monitor		"VP930 Series"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
[COLOR="Red"]    	Option "AddARGBGLXVisuals" "True"
    	Option "DisableGLXRootClipping" "True"[/COLOR]
```

3) Reboot the system and try again. It should appear correctly now I believe.

If your an ATI card, your on your own. I'm an NVidia man...

---

### Post by james.gravley on 2007-06-12
Thanks for the help guys.

I followed the steps and when I click on "enable desktop effects" I get this error

"The composite extension is not available" 

any suggestions?

---

### Post by asymmetric on 2007-06-12
try adding
```

Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

to your xorg.conf, as stated [here]("http://www.nvnews.net/vbulletin/showthread.php?t=77030")

---

### Post by starcraft.man on 2007-06-12
Ok, I think this is a problem with how your xorg was configured. I did a quick search and this answer from ajmorris is good so I'm just gonna quote it. Follow it and make sure you enable the extension then restart the GDM.

> **ajmorris said:**
> ok, go to start menu >> Accessories >> Terminal

Type ```
sudo gedit /etc/X11/xorg.conf
``` (it will ask for a password, and when you type it in the characters appear not to be typing in, but they are)
then down the bottom of the file you have : 

Section "Extensions"
Option "Composite" "Disable"
EndSection

Change it to this:

Section "Extensions"
Option "Composite" "Enable"
EndSection

then restart X, and you will be able to use desktop effects.

Note : Alternatively, instead of using the terminal you can press alt+F2 and type gksu gedit then navigate to and open, from the open dialog box from the file menu, /etc/X11/xorg.conf

That should do it, have fun.

---

### Post by CrispyFried on 2007-06-12
re: temps

have you tried cleaning out your notebooks vents with canned air?

---

### Post by james.gravley on 2007-06-12
I added the section and it worked, thanks guys

I am such an idiot. Sometimes you just don't realize the most simple things. I did the canned air and it help tremendously

The help is much appreciated

---

### Post by starcraft.man on 2007-06-12
> **james.gravley said:**
> I added the section and it worked, thanks guys

I am such an idiot. Sometimes you just don't realize the most simple things. I did the canned air and it help tremendously

The help is much appreciated

You are most welcome. Quality friendly help is what we do :D.

---

