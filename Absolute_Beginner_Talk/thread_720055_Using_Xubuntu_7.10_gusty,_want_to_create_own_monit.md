---
title: "Using Xubuntu 7.10 gusty, want to create own monitor section in xorg.conf"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-09
I'm using Xubuntu 7.10 and I would like to create my own monitor section under xorg.conf.

I will try to give as many details as possible and try to remain as organized as possible at the same time.
[COLOR="Red"]
**_[SIZE="6"]WHAT I WOULD LIKE TO DO AND WHY:[/SIZE]_**[/COLOR]

I'm using Xubuntu 7.10 and I would like to create my own monitor section under xorg.conf.

You're probably thinking to yourself something like, "Why doesn't he just go to Screens and Graphics and play around till he finds one that works?". Well that answer to that simply is that none of them have the DPI I require with said resolution: 1024 X 768. I cannot find a simple guide on editting my DPI. The following link seems to work for most people:

[http://xubuntulinux.blogspot.com/2006/07/ubuntu-set-correct-dpi-for-x-server.html](http://xubuntulinux.blogspot.com/2006/07/ubuntu-set-correct-dpi-for-x-server.html)

Compared to how it loked before (which you'll see if you click any of the links in the History section of this post) the DPI really isn't that bad. Allow me to take you a screenshot:

[http://www.geocities.com/lookin4busstop/wtfthissucks.jpg](http://www.geocities.com/lookin4busstop/wtfthissucks.jpg)

It's just that I have a mother who has to use this computer as well, and her eyesight isn't the greatest. It also gives her more ammunition as to why I should put Windows back on the computer and I'm sure we all know that I don't need that.

[COLOR="Red"]**_[SIZE="6"]HISTORY:[/SIZE]_**[/COLOR]

I suppose you're wondering how I wound up in this predicament. Well, I installed Xubuntu 7.10 on my little brother's MPC Client Pro 345. I doubt any other details of the computer are really that important. Everything looked great on it, however, I decided to install my NVIDIA GeForce 4 MX-SE so that he could play games on his computer. I went through what I thought was a successful install untill I discovered that I could not utilize 3d accelleration for the life of me. More details really aren't that important, but if you would like to know the full story feel free to click here:

[http://ubuntuforums.org/showthread.php?t=717271](http://ubuntuforums.org/showthread.php?t=717271)

which then led to:

[http://ubuntuforums.org/showthread.php?t=718280](http://ubuntuforums.org/showthread.php?t=718280)

and finally:

[http://ubuntuforums.org/showthread.php?t=719227](http://ubuntuforums.org/showthread.php?t=719227)

After I finally got the driver to install correctly with 3d acceleration an option what I thought was that hmmm the system font is now way too small, however, everyone keeps telling me that its actually my DPI that is too small. Thus, the quest for the ability to reset my DPI and discover what I should set it at has begun, and I've since decided that writing my own "driver" or "monitor section" in xorg.conf would be a lot easier.

[COLOR="Red"]**_[SIZE="6"]MY UNDERSTANDING OF THE DPI GUIDES:[/SIZE]_**[/COLOR]

The following guide seems to be working for most people:

[http://xubuntu.wordpress.com/2006/08/09/howto-fix-xfce-fonts/](http://xubuntu.wordpress.com/2006/08/09/howto-fix-xfce-fonts/)

I followed it with out an issue until I got to the thid step which is a link to another guide:

[http://xubuntulinux.blogspot.com/2006/07/ubuntu-set-correct-dpi-for-x-server.html](http://xubuntulinux.blogspot.com/2006/07/ubuntu-set-correct-dpi-for-x-server.html)

Let's try to follow my thoughts as I followed this guide:

First off, it said there was a screenshot for an example.... either I've got a browser issue or there isn't one at all... no worries, let's continue.

Okay, paste a specific command at the end of mousepad ~/.config/xfce4/Xft.xrdb? You got it! Save, exit.

Step two, add a couple more commands under the "files section of my /etc/X11/xorg.conf. You got it! I already got familiar with this file do to the trials and tribulations of my graphics card endeavours. Save, exit.

Step three, Configure my DPI settings in /etc/X11/xorg.conf? .... hmmm well no one told me where that was, and I can't seem to find "DPI" when I search the file.... okay here's a link to another guide... perhaps this one will actually do something!

Okay so I can use

```
xdpyinfo | grep resolution
``` 

and

```
xrdb -query
```

to get current DPI value.

Oh can I?

Fine, first one gave me:
```

resolution:    80x80 dots per inch
```

(actually the first time I did this it gave me 50X50 I suppose when I messed around with Screens and Graphics it changed that, for a report of what my Monitor section looked prior to messing with Screens and Graphics, you can either check my past threads or scroll on down to the "WHAT I DO KNOW:" section.)

is that my DPI? I suppose dots per inch would stand for that... so how do I know what DPI I'm supposed to use? What is that default setting that looked so good on the other computers I've put Ubuntu and Xubuntu on? Too bad I don't have any of them readily available.

The next command, lets see what that gives us:

The first time I did it all it gave me was

```

*customization: -color
```

Due to some steps that are soon to come up mine now says:


```
*customization: -color
Xft:    dpi: 96
```

Then it says:

To change DPI values create a file ~/.Xresources or edit ~/.config/xfce4/Xft.xrdb

Okay I created Xresources... logged out logged back in... nothing... still the same

Lets edit Xft.xrdb

okay lets open it to edit it

okay the contents are:


```
Xft.antialias: 1
Xft.hinting: 1
Xft.hintstyle: hintfull
Xft.rgba: none

```

Yeah, like I really know what to do with that.

Then it said to try adding this to the monitor section of my xorg.conf

```

DisplaySize XXX XXX (in my case it's 270 203)
```

The formula it gives to figure out what XXX XXX is:

XXX is calculated by using formula 25.4 * pixels (height or width) / DPI.

I have absolutely no clue how to find how many pixels 323mm or 245mm is, I googled around and found several different explanations as to how to find it with all different results so I can't finish the equation.

The last thing says:

Note: X Window System has it's own DPI value set in /etc/X11/xorg.conf

Well, we already know I can't find a DPI section anywhere in xorg.conf, so that's out of the question.

...this guide sucks.

_**[COLOR="Red"][SIZE="6"]WHAT I DO KNOW:[/SIZE][/COLOR]**_

Here are my monitor's stats.

To be breif, it is a MPC CM720F 17" Flat CRT OSD Monitor (98kHz) Dark.

To be more detailed:

[http://support.mpccorp.com/apps/specs.asp?ID=7654](http://support.mpccorp.com/apps/specs.asp?ID=7654)

or

Part no.:             MNN001193-00
Automatic Recovery Time -- Off/Sleep Mode:	< 10 Seconds
CRT Dot Pitch:	(Diagonal) 0.25 mm
CRT Size:	17in (16.0in Viewable)
CRT Technology:	Invar Shadow Mask Flat Color CRT
Maximum Resolution:	1600 x 1200
Number of Display Colors:	True Color - 16.7 million colors
Physical Dimensions (H x W x D):	402 x 410 x 420mm
Power Consumption -- Normal Operation:	< 120 Watts typical (Green LED)
Power Consumption -- Off/Sleep Mode:	< 5 Watts (Orange LED)
Scanning Frequency -- Horizontal:	30 - 98 kHz
Scanning Frequency -- Vertical:	50 - 160 Hz
Scanning Frequency: Maximum Pixel Clock:	202.5 MHz
Signal Connector Cable:	Black Captive cable with DB-15 Type video connector (Blue - Pantone #661C)
Signal interface:	Analog
Weight (Kg):	21.0 Kgs

While following the guide I have measured the area of the computer screen in mm which comes to:

323 X 245

Here is what the monitor section of my xorg.conf looks like now:

```
Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

```

Here is what it looked like before I messed around with Screens and Graphics:

```

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
    ModeLine       "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    ModeLine       "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
    ModeLine       "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
    ModeLine       "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

```

If anyone needs anymore detail please feel free to ask, I'm not sure what else I can tell you.

---

### Post by caterpillar322 on 2008-03-09
This may not be the answer you are looking for, but wouldn't raising your font size (Settings> User Interface Settings) achieve what you are trying to accomplish? If this was already mentioned in one of your other posts (I just skimmed over them) I apologize but it seems to me that overall you are trying to make things easier to read for your mom. I hope this helps.  :)

---

### Post by whoscheesemine on 2008-03-10
You're right, it does make things bigger. The problem is it takes what's already normal size, and makes it enormous, while taking what's tiny, and making it normal size.

---

### Post by whoscheesemine on 2008-03-10
Sorry to bump my own, but its kind of urgent.

---

