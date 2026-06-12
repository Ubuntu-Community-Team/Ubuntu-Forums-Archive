---
title: "Screen Resolution Broken???"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by ReaderRat on 2006-10-03
I have just installed Ubuntu 6.06.1 on my brother's new box. He is more visually impaired than I....>50% in one eye. I need 800x600 so he can see the fonts on screen. Using "System > Preferences > Screen Resolution" does not work. It stays on 1280x1024. Am I doing something wrong, or is this a known problem with Dapper? How can I fix it? He really wants to try Ubuntu.

---

### Post by bodhi.zazen on 2006-10-03
Not sure. See if this helps:

[Bodhi.s How-to](http://ubuntuforums.org/showthread.php?t=269052)

Either way, if you would give feedback so I can help others it would be appreciated.

---

### Post by mon_m on 2006-10-03
> **ReaderRat said:**
> I have just installed Ubuntu 6.06.1 on my brother's new box. He is more visually impaired than I....>50% in one eye. I need 800x600 so he can see the fonts on screen. Using "System > Preferences > Screen Resolution" does not work. It stays on 1280x1024. Am I doing something wrong, or is this a known problem with Dapper? How can I fix it? He really wants to try Ubuntu.

What graphics accelerator might you be using?

By the way, Bodhi's thread on resolution problems is top-notch and saved me from hell.  Hence, the new sig.

---

### Post by bodhi.zazen on 2006-10-03
> **mon_m said:**
> What graphics accelerator might you be using?

By the way, Bodhi's thread on resolution problems is top-notch and saved me from hell.  Hence, the new sig.

LOL mon_m :lol: you are too kind !

I am working on the Intel drivers and am not sure if they work. It is a work in progress.

---

### Post by theratster on 2006-10-03
I've done this for a different problem.

You have a file called xorg.conf (Its in your etc/X11 folder I think). Basically, when you scroll down there you will see something like:

"1280x768" "1024x768" "800x600"... etc.

this is for various bit-depths. The first one is the "default". (so delete it, or change it to whatever you want!)

---

### Post by ReaderRat on 2006-10-03
> **bodhi.zazen said:**
> Not sure. See if this helps:

[Bodhi.s How-to](http://ubuntuforums.org/showthread.php?t=269052)

Either way, if you would give feedback so I can help others it would be appreciated.
The quick fix did not work. From xorg.conf:::
> Section "Monitor"
	Identifier	"VX922"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"VX922"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
Now what?

---

### Post by slimdog360 on 2006-10-03
try 'upping' the fonts and icons. You can also make the font larger in firefox by going preferences-->display?(I think)--> then look for the fonts part and click on the advanced button. Use the minimum font size part to make sure all fonts get bigger. 
This way things get bigger but you dont loose the space so much.

You can create a new account for this so that your fonts are normal in your account.

---

### Post by ReaderRat on 2006-10-03
Thanks, but I am already using HiVis Gnome_Big theme. I need for the stuff in Dapper to be larger so he can read them.

---

### Post by bodhi.zazen on 2006-10-03
> **ReaderRat said:**
> The quick fix did not work. From xorg.conf:::

Now what?

I would do two things:
[list=number][*]Reduce your default color depth to 16 (this will make the box faster and a high color depth is not needed due to visual impirment).[*]Use this:[/list]> DefaultDepth 16

Depth 16
Modes "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"

If that is ineffective, video card ?

---

### Post by ReaderRat on 2006-10-03
Thank you, that did it. Kudos to you.

---

