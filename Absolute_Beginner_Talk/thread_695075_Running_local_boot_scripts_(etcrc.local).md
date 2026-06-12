---
title: "Running local boot scripts (/etc/rc.local)"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by zachrey on 2008-02-12
I recently installed Ubuntu 7.10, and each time I attempt to boot the general system it loads until I hit this: Running local boot scripts (/etc/rc.local)

My computer seemingly stops there. If I hit enter, all that happens is the cursor returns. I cannot enter any kind of command on the line (though I can type. There is no output)

When run in recovery mode, I can get all the way to the terminal(?). Well, the area to enter commands. And I can run commands from it.

What's wrong? :=

---

### Post by dstew on 2008-02-12
Probably some script in that folder is causing the problem. Look in the folder and see what is in there to get a clue. From recovery mode, do ```
cat /etc/rc.local
```Post the result here.

---

### Post by zachrey on 2008-02-12
#!/bin/sh -e
#
#rc.local
#
#This script is executed at the end of each multiuser reunlevel.
#Make sure that the script will "exit 0" on success or any other
#value on error.
#
#In order to enable or disable this script just change the execution 
#bits.
#
#By default this script does nothing.

exit 0

---

### Post by mmb1 on 2008-02-12
I had this same problem, how did you install, from a disc?

You may want to see this link:

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by StefanPieter on 2008-03-29
Hey
I just converted my friend to Ubuntu so i installed 7.10 on his laptop and i've been having non-stop problems. I tried the instructions on _ [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)_ but i had no luck. 

The screen with  Running local boot scripts (/etc/rc.local) on it still flashes a few times then nothing.

I don't know how i can setup my mom's pc and mine with little to no effort and this one has been keeping me busy for the last 3 day just to get it going.

PLEASE PLEASE HELP!!!!!!

---

### Post by StefanPieter on 2008-03-29
When i run 

sudo startx

it gives me a read out of whats happening.
It states that there was no screen found
fatal error 104 on X server ":0.0"
even after i setup xserver again and again

---

### Post by StefanPieter on 2008-03-29
i even had a look at my xorg.conf file here it is


Section "Device"

	Identifier	"ATI Technologies Inc ATI Default Card"

	Boardname	"ATI Rage Mobility"

	Busid		"PCI:1:0:0"

	Driver		"ati"

	Screen	0

	Vendorname	"ATI"

	Option		"MergedFB"	"off"

EndSection



Section "Monitor"

	Identifier	"Generic Monitor"

	Modelname	"Custom 1"

  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync

  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync

  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync

  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync

  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync

  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync

  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync

  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync

  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync

  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync

  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync

  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync

  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync

  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync

  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync

  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync

  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync

  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync

	Gamma	1.0

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"ATI Technologies Inc ATI Default Card"

	Monitor		"Generic Monitor"

	Defaultdepth	24

	SubSection "Display"

		Depth	24

		Virtual	1400	1050

		Modes		"1152x864@75"	"1280x960@60"	"1024x768@43"	"1280x1024@60"	"1024x768@60"	"1400x1050@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"

	EndSubSection

EndSection

---

### Post by SpzToid on 2008-03-30
It sounds like you might have a device missing (Ubuntu thinks so). Is Ubuntu expecting some peripheral from an earlier install maybe? Just a guess for you to try.

---

### Post by StefanPieter on 2008-04-04
I think so... It was easier to re-install than sorting it out. Thanks for trying though

---

### Post by andrewabc on 2008-04-07
I have the same problem but I get it when ubuntu is shutting down.

I see a bunch of text that end with [ok] and 1/2 way down the last one says
running local boot scripts (/etc/rc.local)   [ok]

It stays there for about 10 seconds then continues shutting down.

---

