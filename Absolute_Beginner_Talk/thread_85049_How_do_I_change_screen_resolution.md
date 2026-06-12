---
title: "How do I change screen resolution??"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by waimang on 2005-11-01
Hi folks.
I have been using linux as a secondary operating system for 2 years now and this is the first time with Ubuntu 5.04 for intelx86.
Installing this OS was ok but very time consuming and once the GUI was up, the only screen resolutions I could get were 800x600 or 640x480.
My hardware is built just for linux:
1300AMD duron
512Mb DDR pc2100 ram
GF4-MX440-64 Mb
and all other hardware works fine with all other linux flavours.
So my Q,s is what am I doing wrong as I have no idea why Ubuntu does not let me choose my usual 1024x768 @ 85Hz on my ViewSonic 17inch monitor.
I cannot believe Ubuntu would produce a polished OS with such a terrible default screen choice.
Any help would be much appreciated.
P.S. the Ubuntu distribution I have came free from Canonical Ltd.
and my current linux flavours are PUPPY-chubby-1.05 and Kanotix 2005.1.

---

### Post by jeffreyvergara.NET on 2005-11-01
I would highly suggest to use the "search" tool before posting question.
anyways try:

sudo dpkg-reconfigure xserver-xorg

just follow the instruciton

---

### Post by waimang on 2005-11-01
Hi jeffreyvergara.NET.
Thanks for your reply and I will try your suggestion.
However I would like to point out that being able to configure your screen resolution during installation is the "bread and butter" of nearly all recient Linux disto,s.To have to resort to such archaic solution for a Linux newbe is a retro step for such a modern and polished OS like Ubuntu.
I have given away many copies of this OS to friends and associates and we all agree that this flaw in Ubuntu is 5.04 is crazy.
Cheers,
Tim.:???:

---

### Post by poofyhairguy on 2005-11-01
[QUOTE=waimang]Hi jeffreyvergara.NET.
Thanks for your reply and I will try your suggestion.
However I would like to point out that being able to configure your screen resolution during installation is the "bread and butter" of nearly all recient Linux disto,s.To have to resort to such archaic solution for a Linux newbe is a retro step for such a modern and polished OS like Ubuntu.
I have given away many copies of this OS to friends and associates and we all agree that this flaw in Ubuntu is 5.04 is crazy.
Cheers,
Tim.:???:[/QUOTE]


Here is a developer's answer:

[http://ubuntuforums.org/showpost.php?p=459545&postcount=5](http://ubuntuforums.org/showpost.php?p=459545&postcount=5)

---

### Post by blastus on 2005-11-01
I just edit the /etc/X11/xorg.conf file...

```
sudo nano /etc/X11/xorg.conf
```

...I don't fully understand the file but I have modified the "Screen" section. Also, I forget what the menu item is in Ubuntu (because I'm using Kubuntu) but look around in the menus, you should see an item called "Screen Resolution" or something like that that you can change.

BTW, I can't change the screen resolution during an installation of Windows XP either. I can't because I need to install proper NVIDIA drivers as Windows XP does not recognize my video card.

---

### Post by waimang on 2005-11-02
Hi Folks. Thank you all for you reply,s.
Re: blastus. You are right, WinXP does not let you change screen resolution during installing the OS as the driver are installed seperately. However with all the Linux Distro,s I have used to date have the drivers,or generic drivers as part of the Linux OS, Call me blonde if you like but I do not understand how Ubuntu can find my graphics card correctly, then not give me a choise to change the screen resolution to anything other that 800x600 max, which it loads by default, from within the GUI.
Do I have to install nv drivers separately (like microsoft OS,s) or use the command line within a "shell" to configure my resolution manually. 
I also have downloaded Kubuntu 5.10 preview and tried to install this with the same results...perhaps this is a "debian" thing. 
However, all your help is appreciated.
Thanks,
Tim.

---

### Post by steevc on 2005-11-02
[QUOTE=jeffreyvergara.NET]I would highly suggest to use the "search" tool before posting question.
anyways try:

sudo dpkg-reconfigure xserver-xorg

just follow the instruciton[/QUOTE]

I've found that tool has to be used with care. A couple of times I've stopped all X from working by playing with the settings. Luckily I could fix it by running it again with some different settings. Generally I take all the defaults.

---

### Post by blastus on 2005-11-03
I have an 8-year old Samsung SyncMaster 700b 17" monitor.  I also run at 1024x768 @ 85hz. Yes you have to install the NVIDIA drivers after you install Ubuntu. To install them see [Ubuntu Starter Guide - How to install Graphics Driver (NVIDIA)](http://ubuntuguide.org/#installnvidiadriver). The instructions are for Hoary but they work for Breezy also.

Here are the Monitor and Screen sections in my /etc/X11/xorg.conf file:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-69
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
```
I'm not sure exactly where the current screen resolution is set, but the Screen section of the xorg.conf file determines the horizontal and vertical sync rates available along with the available screen resolutions for each color depth. 

What I would do is first install the NVIDIA driver. Then find the horizontal and vertical sync rates for your monitor (it should be in your manual.) Then enter those ranges into the Monitor section in your xorg.conf file similar to the way I have. Then edit the Screen section of your xorg.conf file--since you want to run at the same resolution and vertical sync rate I run at, you could just try using the Screen section of my xorg.conf file. Notice, the DefaultDepth for mine is 16 (which means I run at 16bit colors or 65,536 colors.)

After you do all this, reboot your machine. When you boot up now, you should see an NVIDIA logo appear. Then find the "Screen Resolution" menu item in Ubuntu and change the screen resolution and vertical refresh rate to 1024x768 @ 85Hz respectively.

---

### Post by mechanic on 2005-11-04
What are these archaic 1024x768 17-inch monitors people are using? Surely they all run at 1280x1024 these days?

m.

---

### Post by blastus on 2005-11-04
[QUOTE=mechanic]What are these archaic 1024x768 17-inch monitors people are using? Surely they all run at 1280x1024 these days?

m.[/QUOTE]

Yes they can run at 1280x1024 but NOT at 85hz at that resolution. I believe my monitor supports a maximum of 60hz at that resolution. But anything below 75hz produces eye-straining flicker and is unusable to me, so I use 1024x768. Some of us are happy with our old monitors and we either have the money but don't want to shell out for a new monitor or don't have the money for a new monitor.

---

### Post by mechanic on 2005-11-07
I used to think my Sony Trinitron 17-inch CRT was pretty good till I bought a TFT monitor. The difference in clarity and the vivid colours are incredible, and a decent 17 inch TFT doesn't cost more than 200 pounds! You spend most time staring at the monitor so it makes sense to get that right.

m.

---

### Post by patrick295767 on 2005-11-07
I usually do this way:
  
> 
  I usually use the : 
sudo dpkg-reconfigure xserver-xorg

set only one screen I want 
and then u can select :
simple (screen size)
medium (choose ur resolution)
> expert (lot of to set up) <
  
Pat'

---

### Post by Who on 2005-11-07
Depending on how 'deep' the problem with the resolution is you may be able to fix it with the GNOME Screen Resolution Changer in System-->Settings

---

