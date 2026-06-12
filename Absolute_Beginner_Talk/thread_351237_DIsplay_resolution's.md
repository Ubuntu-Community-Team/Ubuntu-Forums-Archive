---
title: "DIsplay resolution's"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Stumblinforward on 2007-02-01
First let me say that im about 1 hour into this so im as green as they get.
I want to set my display resolution higher that 1024x768, i have a 22" wide-screen acer display and a nvidia gforce 6600 video card. 
I have tried to download the linux driver from nvidia, managed to get it saved to my desktop 
( since i dont have a clue as to how to save it any where else :confused:  ) tried to install and all i got was this error.
[B][I] gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/I][/B]. now i tried the other character coding and got nothing there. 
I have been wanting to learn how to use linux for a while so i think you may be hearing from me often so please be patient. 
Any help would me great.

---

### Post by maruchan on 2007-02-01
Hi, could you please post the file /etc/X11/xorg.conf here so we can take a look at your graphics settings? Thanks.

PS Should be no problem getting your monitor working at full res. My 24" lcd works like a charm. :)

---

### Post by maruchan on 2007-02-01
BTW, don't try to use the linux driver from nvidia. Do this instead:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

After that we just need to get the right monitor settings into your xorg.conf. Basically I think you can use these settings (replace whatever's in these sections already):

**I googled your monitor's make and model with the phrase "xorg.conf" to find the settings below.**

(note: type Alt+F2 and then "gksudo gedit /etc/X11/xorg.conf" to make these changes)

```
Section "Monitor"
	Identifier	"Acer AL2216W"
	Option		"DPMS"
        HorizSync       30-83
        VertRefresh     60
        Modeline        "1680x1050_60.00" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"WARNING PUT THE NAME OF YOUR VIDEO CARD HERE EXACTLY AS FOUND IN THE DEVICE IDENTIFIER SECTION OF THIS FILE, AFTER YOU INSTALL THE NVIDIA DRIVER FOR YOUR 6600"
	Monitor		"Acer AL2216W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Be sure to restart your comp after making these changes.

---

### Post by maruchan on 2007-02-01
PS Don't take this the wrong way, but I noticed you went to NVidia's site to find a driver for your card. This is a very Windows-based approach and tends to complicate things if applied to Ubuntu. 

Most of these common desktop tasks are easy to do in Ubuntu without hopping on the net to go search for drivers/games/files/etc.

The upside of this approach (the Ubuntu way) is that you allow Ubuntu to manage updates for you, so later on when you upgrade your system, you can upgrade *all* the software on your machine at the same time. It works really well.

So, try looking at ubuntuguide.org for stuff you're trying to do as you set up your system. The guide will tell you how to use tools like apt-get to set up software quickly without doing any web searching. :)

I'm just saying this because I had to learn the hard way by messing up my system a bunch :)

---

### Post by Stumblinforward on 2007-02-01
Thanks!! 
This worked perfectly.
Just copy and pasted it in and changed the "device". thanks for the help

---

### Post by maruchan on 2007-02-02
No problem, glad it worked!

More notes for any visitors with similar problems: You need the following info to get your screen resolution right:

-Make and model of video card
-Make and model of monitor

Then, you **must** configure both monitor and video card. Installing video card drivers alone **won't** be sufficient. 

Specifically, you need to know those HorizSync and VertRefresh lines for your monitor (if you have refresh rate problems these are also a common culprit - your numbers may be incorrect). They can usually be found in the manual for your monitor. Or try googling "[monitor make/model] xorg.conf" to see if anybody else did the work for you.

**The ideal scenario:** Search via Google for an xorg.conf file that matches your monitor's make and model! Then paste the relevant sections into your /etc/X11/xorg.conf file. Follow the ubuntuguide.org guides to set up your video card driver.

---

### Post by NorthernPaladin on 2007-02-02
Well, my problem is that I don`t know the model of my monitor, and I don`t have a manual, is there any way to find it out?
EDIT: There is a sticker in the back of the monitor. Do I find the needed info there? And what I exactly need from there? There is a lot of numbers and stuff in there

---

### Post by maruchan on 2007-02-02
Post *any* information you have on your monitor, especially any text on your monitor's case.

---

### Post by RythmDivine on 2007-02-02
I have similar problems with a fresh install of edgy:

Monitor is a Viewsonic VG700b
Graphicscard is a ATI Radeon 9800 <-not PRO

After installation i have a blurry screen. The refreshrate is -19557 Hz (yes, it is a minus!)

so i google a bit and find that i should

sudo gedit /etc/x11/xorg.conf

and there add the resolution and refreshrate manually under the heading Monitor.

Problem is, when i do that i get a blank xorg.conf i Gedit. If i open xorg.conf by doubleclicking it in the folder, i get (i presume) the proper xorg.conf. But if i edit that one i cant save because i lack permission to do so.

I also tried to use terminal with

gksudo gedit /etc/x11/xorg.conf
sudo nano /etc/x11/xorg.conf

with same result, a blank xorg.conf. what do i do wrong?

Edit: of course it helps if you type X11 instead of x11. problem solved.

---

### Post by NorthernPaladin on 2007-02-04
Well, my problems with the monitor continue, this has nothing to do with linux, its just broken. Its gonna go KABOOM any minute now, so tomorrow I will go to a shop and buy a new one

---

### Post by shareMenaPeace on 2007-02-04
> **RythmDivine said:**
> 
I also tried to use terminal with

gksudo gedit /etc/x11/xorg.conf
sudo nano /etc/x11/xorg.conf

with same result, a blank xorg.conf. what do i do wrong?

Edit: of course it helps if you type X11 instead of x11. problem solved.

Linux is Case Sensitive, so you need to type /etc/X11/xorg.conf

A blank file indicates you have not the file you want.

---

### Post by NorthernPaladin on 2007-02-09
Ok, now I have a new monitor. Maker is V7, model is L17GM, and I have the manual. I`ll post part of it so you can look at it. Does it have all the info needed?

Edit: here is their website [http://www.v7-world.com/606c1266-906a-11db-9c96-00304856c39e?action=show_product_details&category_id=4c1d3d0d-9066-11db-9520-00304856c39e&product_id=4c60aece-9066-11db-9520-00304856c39e](http://www.v7-world.com/606c1266-906a-11db-9c96-00304856c39e?action=show_product_details&category_id=4c1d3d0d-9066-11db-9520-00304856c39e&product_id=4c60aece-9066-11db-9520-00304856c39e)

---

