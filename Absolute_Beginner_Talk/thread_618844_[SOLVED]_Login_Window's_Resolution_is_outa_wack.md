---
title: "[SOLVED] Login Window's Resolution is outa wack?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-11-20
I don't know how to discribe properly, so I took some photos...

1. Notice in this photo the black bar on the left side of the screen, also there appears to be icons/buttons on the bottom left and right of the screens but they aren't fully on the screen.
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/th_IMG_2620.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/xubuntu/IMG_2620.jpg)
*(Click to see larger format)*

2. Notice in this photo (after I am logged on) the resolution is just fine and dandy :) Everything fits perfectly.
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/th_IMG_2621.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/xubuntu/IMG_2621.jpg)
*(Click to see larger format)*

Why is the login screens resolution all outa wack, and how can I fix it?
Thanks in advance,
-BassKozz

---

### Post by karrank% on 2007-11-20
can't help other than to add  that I've got it and don't know why either. Not functionally a problem but bothersome since it's inexplicable.

---

### Post by websnail on 2007-11-20
It seems like the default resolution problem.
edit your xorg.conf file with root ,and remark all modes except the one matchs physical resolution of your LCD in section "screen" and section "monitor" 
> sudo gedit /etc/X11/xorg.cong
like this :
```
Section "Monitor"
	Identifier	"&#36890;&#29992;&#26174;&#31034;&#22120;"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
#	Vertrefresh	56.0 - 65.0
	Vertrefresh	60
[COLOR="Red"]#  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
#  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
#  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync[/COLOR]
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [GeForce Go 7400]"
	Monitor		"&#36890;&#29992;&#26174;&#31034;&#22120;"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800@60"	
[COLOR="Red"]#"1280x720@60"	"800x600@60"	"1280x800@60"	"800x600@56"[/COLOR]
	EndSubSection
EndSection

```
have a try!

---

### Post by BassKozz on 2007-11-20
Thanks for the help websnail, but I my ***xorg.conf*** looks nothing like yours...```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV6 [Vanta/Vanta LT]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

```
Should I add these resolution lines (modeline) like you have setup in yours...
p.s. I am using Xubuntu if that makes a difference.
Thanks again,
-BassKozz

---

### Post by websnail on 2007-11-21
> **B/-\ssKozz said:**
> Thanks for the help websnail, but I my ***xorg.conf*** looks nothing like yours...```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV6 [Vanta/Vanta LT]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

```
Should I add these resolution lines (modeline) like you have setup in yours...
p.s. I am using Xubuntu if that makes a difference.
Thanks again,
-BassKozz

No matter what *buntu you use , xorg should be same . what I mean , just try . however , it can't be worse , right ?:guitar:

---

### Post by Papillonrus on 2007-11-22
It is not a default resolution problem with xorg.conf.  It is a problem in the login screen Resolution which can be changed by adding a file to reset that resolution.  As soon as I find it again I will post it.

---

### Post by BassKozz on 2007-11-22
> **websnail said:**
> No matter what *buntu you use , xorg should be same . what I mean , just try . however , it can't be worse , right ?:guitar:
I've tried a bunch of different settings and none of them would work :(
> **Papillonrus said:**
> It is not a default resolution problem with xorg.conf.  It is a problem in the login screen Resolution which can be changed by adding a file to reset that resolution.  As soon as I find it again I will post it.
Please Do...
Patiently awaiting your reply [-o<

---

### Post by BassKozz on 2007-11-25
> **Papillonrus said:**
> It is not a default resolution problem with xorg.conf.  It is a problem in the login screen Resolution which can be changed by adding a file to reset that resolution.  As soon as I find it again I will post it.

Any luck finding that file Papillonrus?

---

### Post by websnail on 2007-11-26
Hi&#65292; Do you try "Nvidia-settings" ? if your use drive "nvidia-glx" , maybe you need install "nvidia-settings" , with "nvidia-glx-new" it may installed already . this can setup your "xorg.conf" easyly.

---

### Post by websnail on 2007-11-26
picture of nvidia-settings

---

### Post by BassKozz on 2007-11-26
I am using 'nvidia-glx-kegacy' because this is a very old computer, I tried 'nvidia-glx' and 'nvidia-glx-settings' but it only made matters worse, even to the point where I couldn't even see windows after login because the resolution was so low... so I did some searching on how to fix resolution problems, and I found this little tool: "sudo dpkg-reconfigure xserver-xorg", after a couple of tweaks I finally got it working properly :D

Thanks for the help

---

