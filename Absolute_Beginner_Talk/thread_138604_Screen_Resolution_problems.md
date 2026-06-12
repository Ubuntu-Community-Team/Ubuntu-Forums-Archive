---
title: "Screen Resolution problems"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by B7may on 2006-03-02
It seems many people have this same problem and I have looked through and tried to fix it with no luck.  I have a Dell flatscreen monitor (E153FP) and I can only get 800 x 600 resolution.  I do not have the option to change it to anything higher.  From what I have found it may have something to do with the refresh rates, but I am nervous about changing them.  I read in one post that I can ruin my monitor?  Anyhow, the monitor says it will support 1024 x 768 at 60Hz.  Right now it is running 800 x 600 at 60Hz.  

From another post I looked at /var/log/Xorg.0.log and found the following information (I don't know if it helps).
(II) CIRRUS(0): Not using mode "1024x768" (illegal vertical timings)

But I also found the line that says
(II) CIRRUS(0): Not using default mode "800x600" (vrefresh out of range)


But that is what I am using??


Here is my xorg.conf file (concerning the monitor section)

Section "Device"
	Identifier	"Cirrus Logic GD 5465 [Laguna]"
	Driver		"cirrus"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
	Modeline "1024x768" 17.04 1024 1032 1056 1096 768 768 768 777 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Cirrus Logic GD 5465 [Laguna]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by Sandlst on 2006-03-02
I have to fix my screen resolution with every install, this method works fine for me:

first make a backup of xorg in case it should fail to start:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then do this:
```
sudo dpkg-reconfigure xserver-xorg
```
It will prompt you for a bunch of stuff, if you've installed new video drivers you should select those in the very beginning, for the rest default options should give no problems- it will get to a point that it asks you what resolutions you want the x-server to use, select the ones you want, but make sure to scroll down the list of resol. as it auto checks three at the very bottom you cant see unless you scroll down- in theory, these shouldn't matter since it automatically uses the highest avaliable, but un-checking these is the only way I've gotten it to work right on my computer-after it finishes, restart x with crtl+alt+backspace, if x fails to load put this into the command prompt:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```, then:
```
sudo /etc/init.d/gdm restart
```(or kdm if using kde)
if all works right you may have to still change your resolution from the menu (system/prefences/screen resolution)  I hope this works, good luck, and post back if you have any problems.

---

### Post by ahh_dee on 2006-03-02
i have to give this a shot also thanks

---

### Post by pcolamar on 2006-03-02
Hi,
  I have a similar problem with my NecP1150 & MGA G100 card.

Although my xorg.conf contains the mode 1280x1024:

SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" .....etc.......

and the DefaultDepth is correct:

DefaultDepth  24

The menu (system/prefences/screen resolution) does not show up any resolution higher than 1024x768 at any refresh rate.

Any hint on how can I get at least the 1280 x 1024 working ?

Thanks

Palmer

PS I tried what Sandlst suggested above. Situation does not change
PPS In windows the 1280x1024@75Hz 24bits works fine

---

### Post by frodon on 2006-03-02
You just need to put the good refresh rates in your config file, a quick google search will tell you what are the values for your monitor and you MUST use these values and nothing else, when you have the values change your  HorizSync and VertRefresh parameters to these values ... that's all you need.

Do you know the exact name of your screen ?

---

### Post by pcolamar on 2006-03-02
Actually I did that with :

dpkg-reconfiguration xserver-xorg

I entered the correct ranges.

Going deeper in the Xorg.0.log I see that hsync and vsync are correct but close to any of the 1280x1024 mode there is the message:

(II) MGA(0): Not using default mode "1280x1024" (insufficient memory for mode)


But the card has 4MB on board and I manually setted to 4096KB in the reconfiguration, on the other side, as I said prev.ly, the 1280x1024@75Hz 24 bits is properly working in Win.XP.

Where can I check if the 4MB are really recognized by the xserver ?

Cheers

Palmer
PS the screen is a NEC P1150 that goes 55-160Vsync & 31-94 Hsync

---

### Post by B7may on 2006-03-02
Every time I have a problem I go around for hours.  Then, when I finally fix it, it is something so simple.

I searched the internet and found a document that showed the refresh rates for my moniter.  I also found out how much memory my video card had.  i ran the program:
sudo dpkg-reconfigure xserver-xorg
and went through the menus.  I typed in the correct value for memory on my car.  When it came to video setup I clicked the "advanced" options and typed in the numbers from the data sheet on the computer.  Re-ran everything and it works now.  It seems like I have done that 100 times, but oh well - I learn something every time.

---

### Post by Rhyader on 2007-10-29
RE: Screen Resolution problems
"Sandlst"
> I have to fix my screen resolution with every install, this method works fine for me:
> ... dpkg-reconfigure xserver-xorg ...

IT WORKED !!!
Thank You!

Now I have 1280X1024 in Ubuntu instead of 1024X768

---

