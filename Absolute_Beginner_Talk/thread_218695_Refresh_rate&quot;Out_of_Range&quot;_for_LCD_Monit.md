---
title: "Refresh rate&quot;Out of Range&quot; for LCD Monitor at log-in"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by pmueller on 2006-07-18
Hello,

I have an HP 15 inch LCD monitor that is supposed to not exceed a 60 htz refresh rate. During log-in, my monitor flashes on the screen that my setup at a refresh rate of 75 htz is "out of range" and that the proper range is 60.

Once I type my password, Ubuntu returns automatically to my preferred saved setting of 60 htz. How can I get my log-in screen to start each time at 60 instead of 75?


On the net, some say that running an LCD a a refresh rate above the manufacturer's recommendation can shorten monitor life.

Can you help me solve this log-in refresh rate inconsistency? Thanks.

Paul in New Hampshire

---

### Post by Qrk on 2006-07-18
Use ```
sudo dpkg-reconfigure xserver-xorg
```

to configure your monitor easily. You can change the refresh rate by slelecting the Medium, rather than advanced, mode about 2/3 into the dialog boxes.

---

### Post by codejunkie on 2006-07-18
> **pmueller said:**
> Hello,

I have an HP 15 inch LCD monitor that is supposed to not exceed a 60 htz refresh rate. During log-in, my monitor flashes on the screen that my setup at a refresh rate of 75 htz is "out of range" and that the proper range is 60.

Once I type my password, Ubuntu returns automatically to my preferred saved setting of 60 htz. How can I get my log-in screen to start each time at 60 instead of 75?


On the net, some say that running an LCD a a refresh rate above the manufacturer's recommendation can shorten monitor life.

Can you help me solve this log-in refresh rate inconsistency? Thanks.

Paul in New Hampshire
run ```
sudo gedit /etc/X11/xorg.conf
```in a terminal this will open a file now find this section
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Monitor		"DCLCD DCL9A"
	[COLOR="Red"]DefaultDepth[/COLOR]	24
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
		Modes		"[COLOR="Blue"]1280x1024_60[/COLOR]" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```
look at the [COLOR="Red"]DefaultDepth[/COLOR] mine is set to 24, you add the refreshrate to the resolution your use in the line for your color Depth. so if you want 1024x768 @ 60 hz with 24 bit color you go to the line that has a Depth of 24 and change the resolution to 1024x768_60 save the file and restart the xserver by logging out then press ctrl+alt+backspace this should keep the refresh rate at 60hz hope this helps.

---

### Post by pmueller on 2006-07-19
Hello Again,

I have tested the two pieces of advice  and I am reporting progress but not complete success.

I tried to do what "Codejunkie" told me to do, but did not get good results. In fact, my screen resolution became worse.  It dropped down to 832 x 624 at a 75 refresh rate at the login and regular operations.  I went through the directions twice and got the same results.

Next, I tried the advice from Qrk. This time I had more luck.  My log-in screen is now at the proper resolution and refresh rate. Success, but not complete.

Experimenting, I decided to turn off my monitor and turn it back on during the Ubuntu load up screen after the bios routines, but before the log-in screen.  My HP monitor reported that the Ubuntu loading screen was "Out of Range" with a resolution of 740 x 400 and the refresh rate of 70 htz. I need 60 htz.

Is this a reportable bug? Are there any more ideas? The two other suggestions helped me explore new areas of the Linux/Ubuntu operating system.  Thanks.

Paul

---

### Post by dj3 on 2007-07-29
Hello, pmueller!

Do you have an ATI card? I had virtually the same problem as you with “refresh rate out of range” with FS P17-1.

I think I found a solution for me: just installed the  the proprietary ATI driver “fgrlx” from the Ubuntu repository:

Senaptic:
 ```

xorg-driver-fglrx 
linux-restricted-modules-generic

```

than I changed in in **xorg.conf** the driver in the  “Device” section from “ati” to “fglrx”, so that the section looks something like this:  

> 
Section "Device"
[INDENT]Identifier      "ATI Technologies, Inc. Radeon 9500 Pro (R300 AD)"
Driver          "fglrx"
BusID           "PCI:1:0:0"[/INDENT]
EndSection



The result: the frustrating “out of range...” messages gone for ever.  As a nice side effect is that now I can  adjust the refresh rate with the mouse in Gnome settings.

I hope this will be useful!
Best regards,
dj3

---

### Post by redrogo15 on 2007-08-05
> **codejunkie said:**
> DefaultDepth[/COLOR] mine is set to 24, you add the refreshrate to the resolution your use in the line for your color Depth. so if you want 1024x768 @ 60 hz with 24 bit color you go to the line that has a Depth of 24 and change the resolution to 1024x768_60 save the file and restart the xserver by logging out then press ctrl+alt+backspace this should keep the refresh rate at 60hz hope this helps.


thank you codejunkie, your clear directions enabled me to sort my "Out of Range" problems.

Regards,
Ron               :)

---

### Post by Canarygsr on 2007-08-07
can I make the splash/Login screens a different res to what I run my desktop at?

I cant read the login screen at the moment, its way to small (I cant realy read text on the plasma screen unless I use a low res)

---

