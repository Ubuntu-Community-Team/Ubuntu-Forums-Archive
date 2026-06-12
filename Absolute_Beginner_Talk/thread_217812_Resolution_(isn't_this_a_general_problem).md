---
title: "Resolution (isn't this a general problem)"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Kevf on 2006-07-17
I've used the search-options several times now, but all I could find where specific solutions to a problem with a specified chipset and monitor. 

So I can't come up with an other sollution but to post my specs and problem:

Problem: highest res possible is 1024x768

Spec:
Chipsset Ati Radeon Xpress 200
Monitor Ilyama Vision Master 1451

Hope you guys can help me out. :-D

---

### Post by ahaslam on 2006-07-17
You're probably using the 'vesa' display driver, which limits the resolution to 1024x768. To check, open your xorg.conf file (/etc/X11/xorg.conf) and look under the "Device" section. If you're using the 'vesa' driver, you'll need to install the correct drivers for your particular hardware, to enable a higher resolution.


Tony.

---

### Post by ovimunt on 2006-07-17
Hi,

I'll give you 2 solutions so you can choose whichever suits you. Oh, and by the way, ATI Radeon Xpress X200 is the motherboard chipset NOT the graphics card. I know this for sure because I've got a laptop with the exact same chipset but with an ATI Radeon Mobility X700 graphics card.

Anyway, the first option is to open a file called ***xorg.conf*** and do some tricks around there. Yet, if you are using the VESA driver this might not work. Still, I think it's worth to give it a go.

First, open the file for editing:

> sudo gedit /etc/X11/xorg.conf

Now scroll down the file untill you find some lines that look similar to these:

> 
Section "Screen"
[INDENT]Identifier	"Default Screen"
Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
Monitor		"Generic Monitor"
DefaultDepth	24
SubSection "Display"
[INDENT]
Depth		1
Modes		"1024x768" "800x600" "640x480"
[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Depth		4
Modes		"1024x768" "800x600" "640x480"[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Depth		8
Modes		"1024x768" "800x600" "640x480"[/INDENT]
[INDENT]EndSubSection
SubSection "Display"[/INDENT]
[INDENT]Depth		15
Modes		"1024x768" "800x600" "640x480"[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Depth		16
Modes		"1024x768" "800x600" "640x480"
[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Depth		24
Modes		"1024x768" "800x600" "640x480"[/INDENT]
EndSubSection[/INDENT]
EndSection

As you can see this is where the available resolutions are defined. All you nees to do is to add some other resolutions to the list i.e. ***"1280x1024"***. Then save the file and restart.

Now this solution may or may not work. In any case I would recommend that you also go through the second solution anyway.

This is to install the ATI proprietary drivers. Follow this link and go to ***Method 2***.

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

GOOD LUCK!

---

### Post by Kevf on 2006-07-18
Tnx, going to try it this evening.

---

