---
title: "Back again, but with problems again."
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-12-05
Okay, this time I'm taking detailed notes of everything I do from format to everyday use. I switched back to Ubuntu because I like it better and World of warcraft, my lead anchor to windows, has run out of time again.

I haven't yet started running through the wiki so if the question seems easily answered, I'll probably find it quick enough. Any links would be appreciated greatly though-- Ubuntu has a strong community that makes me feel warm and fuzzy inside <3 *ahem* ...To business. I'm running Hoary Hedgehog, patched as far as it'd let me go.

Things I need to do:

I have a nVidia Vanta (lol) PCI card in my system, and Ubuntu displays on that. I also have a nVidia Geforce 5200 AGP, which my second (and third, if I can get a DVI converter) montiors are plugged into. I've read Unbuntu / Linux support multiple displays well, but where do I go to get this running?

Recompiling my kernel was a cool way to bump up my performance on my aging system (1.15GHz AMD)... Can I do this with multiple monitors (it seemed tied to display), can I replace my video card(s) after I compile a new kernel? Where can I find that very helpful how-to that took me through it last time (Dapper drake has made the forums all reorganized)

Question: My system isn't the worst, but I'm humble with it and don't think highly of it most of the time. Is Dapper drake going to run well on it? Is it worth upgrading (it seems a tad experimental).

This one's dumb... Somebody point me in the direction of the fstab instructions.

Is there a quicktime plugin for Mozilla / Linux? I miss my YTMND's, heh.

Samba server never worked especially well from the wiki instructions last time I tried this OS, can somebody throw a indepth samba troubleshoot / howto at me?

My box:
1.15GHz AMD 32bit, 768MB DDR RAM, 4gb (Pri Master) 20gb (Pri slave) 7200RPM drives. nVidia GeForce 5200 128MB AGP 8x. 
The case is pretty though, all red and jagged with neons. Should have focused on the insides more...

Thanks for any help guys, I really like this community, we get stuff done. Maybe one day I'll be helpful, heh... Think of it as an investment. ...Yeah, that's it.

---

### Post by Nequeo on 2005-12-05
Okay... I can answer a couple of your questions.

For multiple monitor support, you'll need to edit /etc/X11/xorg.conf by hand.

There are instructions in the Nvidia settings guide, which you can find here:
/usr/share/doc/nvidia-glx/nvidia-settings-user-guide.txt.gz 

It's zipped... so you'll need to unzip it before you edit it. I'm going to assume you know how to do that, but if you don't, just ask, and we'll take you through it step by step. Just search the guide for 'Twinview', and follow the instructions there. If you get stuck, just post. 

And your fstab file will be '/etc/fstab'

Cheers!

---

### Post by nerdman on 2005-12-05
wtf, wiki.ubuntu.org is now in italian or something. Where was that FAQ...

Nequeo, this X11 stuff looks dangerous. Anyone have tutorial / experience? I hate formatting ><

lol found the fstab. One problem down :p

---

### Post by Nequeo on 2005-12-05
There's always [www.ubuntuguide.org](www.ubuntuguide.org) ... But that's for Ubuntu 5.04. So a fair bit of the stuff there is out of date.

You could try "Easy Ubuntu" [http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta](http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta)

Which should set up a lot of the media/browser stuff for you automatically.

As far as Xorg stuff is concerned, I haven't found a good tutorial on the web yet. Maybe I'll write one?

Anyway... I don't know how to use multiple video cards to create a dual-monitor set-up. However, I can tell you how to get two monitors going on the Nvidia AGP card. 

Before we start! Make a backup of your xorg.conf file. Copy it somewhere nice and safe. Now, lets's begin. 

Firstly. Have you installed 'nvidia-glx'? If you haven't, type:

'sudo apt-get install nvidia-glx' from the command line. If you're asked for a password, enter your own.

After it's installed, type:
'sudo nvidia-glx-config enable'

That will enable 3d acceleration for your Nvidia card. Next step is to add in the second screen!

From the command line, type:

sudo gedit /etc/X11/xorg.conf

Then search for the section that begins with:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "SyncMaster"

```

Obviously, yours will be slightly different...

directly underneath 'Monitor', add in the following lines:

```

        Option          "TwinView"
        Option "SecondMonitorHorizSync"         "30-65"
        Option "SecondMonitorVertRefresh"       "59-75"
        Option "MetaModes"      "1280x1024, 1280x1024"

```

Of course, this assumes you have two 17" LCD flatpanel screens. If you don't, you might need to change the resolution, of the HSync and Vsync numbers.

Also, this will probably only work if the AGP card is your primary display. 

When you're done, save the file and hit Ctrl+Alt+Backspace to restart the X-server.

If you screw it up, just fiddle with the settings and try again. And if you can't get it going, restore your backup xorg.conf file and try again later...

Hope this helps a little.

Cheers,

---

### Post by MonolithTMA on 2005-12-05
[QUOTE=nerdman]wtf, wiki.ubuntu.org is now in italian or something. Where was that FAQ...
[/QUOTE]

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) :)

---

### Post by nerdman on 2005-12-06
so, before I play with monitor configurations, would I have any benefit from upgrading to dapper drake? :p 

And the Quicktime for mozilla is for windows / apple. :(

---

### Post by Estariel on 2005-12-06
Don't upgrade to Dapper!

It is broken twice a day (badly, e.g. X not working, etc.), and if you can't figure out how to fix those problems yourself, you won't be able to use your computer for anything productive.
I think upgrading to dapper will be safe in about 4 months or so...

---

### Post by nerdman on 2005-12-06
Okay, no dapper drake. sigh, school, that period of unproductivity that eats my day away five times a week... All for a piece of paper that says I'm smart. Hail america. *cough*

When I get home I'm going to install nvidia and play with X11, then recompile kernel-- Where's the tutorial to do the kernel?

---

### Post by nerdman on 2005-12-06
[http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

so I can find it when I get home.

---

### Post by Joe_CoT on 2005-12-06
[HOWTO: Kernel Compilation for Newbies](http://ubuntuforums.org/showthread.php?t=85064). All the guides can be found in Customization Tips & Tricks

---

### Post by matthewstory on 2005-12-06
If you're running Hoary you should upgrade to Breezy, but not to dapper.  In terms of setting up the multiple screens there are a couple of places you can look:

[http://www.ublug.org/ubuntu/twinview...to-breezy.html](http://www.ublug.org/ubuntu/twinview...to-breezy.html)


[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

these are two that are helpful.  As far as tweaking your xorg.conf file it shouldn't depend too much on what version of ubuntu you're running.  Don't worry about configuring it, just always make sure that before you do anything you save a backup copy as something memorable like: 

xorg.conf.back

and if it doesn't work use the cp command to replace the xorg.conf file with the xorg.conf.back file.

regards,
matt

and

---

### Post by nerdman on 2005-12-06
Looking over the gentoo dual monitor site, and deciding that my third display will be worked in not too long from now, I probably shouldn't use 'twinview' as that implies only two.

This is the section for my Video devices, and it tells me it can't find any screens when I try to use it. It is now called 'xorg.conf.broke' in my /etc/X11 directory, since... it was broke :p
```

Section "Device"
	Identifier	"NVIDIA Corporation NV6 [Vanta/Vanta LT]"
	Driver		"nvidia"
	BusID		"PCI:1:7:0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation GeForce 5200"
	Driver		"nvidia"
	BusID		"AGP:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PionexMonitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Monitor"
        Identifier      "DellMonitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"VantaScreen"
	Device		"NVIDIA Corporation NV6 [Vanta/Vanta LT]"
	Monitor		"PionexMonitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "PionexMonitor"
	Screen		1 "DellMonitor" RightOf "PionexMonitor"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

suggestions?

edit: Oh yeah, the AGP card didn't install with Ubuntu since my bios was incorrectly configured. Fixed that... now it boots on the AGP and switches to the PCI when the login screen comes up, lmao... The DellMonitor is on the AGP GeForce card, and X server isn't liking it =(

---

### Post by nerdman on 2005-12-07
ugh, bump ;_;

---

