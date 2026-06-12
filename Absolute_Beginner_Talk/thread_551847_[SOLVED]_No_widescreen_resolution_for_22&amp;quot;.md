---
title: "[SOLVED] No widescreen resolution for 22&amp;quot; generic monitor"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-09-15
[SIZE=4][B]UBUNTU
[/B][SIZE=2]Freshly upgraded to Gusty Gibbon 7.10 (2007-09-15).[/SIZE]
[B]
MONITOR[/B]
[SIZE=2]KDS K22MDWB
*site: [http://www.kdsusa.com/K22mdwb.asp](http://www.kdsusa.com/K22mdwb.asp)*

Supported resolutions:
1680 x 1050 @ ~60Hz
1440 x 900 @ ~75Hz & ~60Hz
1280 x 1024 @ ~75Hz & ~60Hz
1024 x 768 @ ~60 & ~75Hz
[B][SIZE=4]
VIDEO CARD
[/SIZE][/B][SIZE=4][SIZE=2]Intel [/SIZE][/SIZE][/SIZE][/SIZE]82845G/GL (integrated)
[SIZE=4][B]
X.ORG
[/B][SIZE=2]xserver-xorg 7.2-5ubuntu9
xserver-xorg-video-**intel** 2.1.1-0ubuntu2

[SIZE=4]**NOTES**[/SIZE]
Currently, 1280x1024 seems to be working, but of course, that means it is stretching. When ever I use 'System > Administration > Screens and Graphics', it shows 1680x1050 and 1440x900 as I set 1440x900 as the default whilst running 'dpkg-reconfigure xserver-xorg' as root, but when I select either two, the screen goes fuzzy & gray and I am able to hit the cancel dialogue, but that's it.

Do I have a chance at even running this monitor properly with a Intel 845?

Just as a note, Feisty and it's [/SIZE][/SIZE][SIZE=4][SIZE=2]'dpkg-reconfigure xserver-xorg' wasn't working either, so I made the desperate attempt to upgrade. Nothing else is wrong however and it seems to be running quite smoothly.
[/SIZE][/SIZE]

[SIZE=4]**SECONDARY PROBLEM**[/SIZE]
'usplash' doesn't seem to be able to run on boot up or shut down. I thought it was because of debugging I did in the past to take 'quiet' out of the kernel sequence, but that turned out incorrect.

Here's an excerpt of my /boot/grub/menu.lst:
```
title           Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-11-generic root=UUID=3785425a-f8f7-4203-b659-3af098c2614e ro quiet splash
initrd          /boot/initrd.img-2.6.22-11-generic
quiet
```
I figure it has to do with the resolution problem and thus doesn't need a second thread.

---

### Post by w4ett on 2007-09-15
Widescreen on Intel chipsets can be a problem.  Some users have had luck using the 915 Resolution Tweak:

[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

---

### Post by alienexplorers on 2007-09-15
Your video card is suppose to allow the following modes:
> It comes equipped with a 82845G/GL
[Brookdale-G] Chipset for video which provides the following video mode
capabilities:
640 x 480, 16M colors (60, 72, 75, 85, 100, 120 Hz)
800 x 600, 16M colors (60, 72, 75, 85, 100, 120 Hz)
1024 x 768, 16M colors (60, 70, 75, 85, 100,120 Hz)
1152 x 864, 16M colors (60, 70, 75, 85, 100 Hz)
1280x 1024, 16M colors (60, 75, 85, 100 Hz)
1600 x 1200, 16M colors (60 Hz)
1920 x 1440, 64K colors (60, 75 Hz)
2048 x 1536, 64K colors (60 Hz)

---

### Post by uglykigjoe on 2007-09-15
should I suggest ,
to change your Vertical Refresh Rate and Horizontal Sync Rate
(as suggested by the monitor`s manufacturer) in your 
/etc/X11/xorg.conf file. (dont forget to make backup).
It did settle my ACER AL1917W monitor resolution issues.
Hope this helps you too.
:razz:

---

### Post by altonbr on 2007-09-16
> **w4ett said:**
> Widescreen on Intel chipsets can be a problem.  Some users have had luck using the 915 Resolution Tweak:

[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

I tried this last night (forgot to make a post), but to no avail. I'll keep fiddling with it though.

I'll then try and see if it can run 1600x1200, and then try the manufacturer vert. and hor. refresh rate, thank you.

---

### Post by altonbr on 2007-09-16
Here's my /etc/X11/xorg.conf:

I can't seem to get any suggestions working, whether using 'intel' or 'i810' drivers, '16' or '24' bit colour or '1600x1200' or '1680x1050' resolutions.

I think the i915resolution hack looks like my best bet although Ubuntu 7.10 has it implemented as the 'intel' driver.

You can read about Intel's hard work and debugging here: [http://intellinuxgraphics.org](http://intellinuxgraphics.org)

If you go here: [http://www.intellinuxgraphics.org/user.html](http://www.intellinuxgraphics.org/user.html) you can read their thoughts on getting it running in Ubuntu 7.04:

> Need to reconfigure with "sudo dpkg-reconfigure xserver-xorg", this error corrected in the upcoming release (7.10). Only the i810 driver works, only with 16bit mode because in 24bit mode the banding of gradients and false colours make this chipset unusable for graphical works. With xorg's intel module only blank screen the result.

**[SIZE="4"]X.ORG CONF[/SIZE]**
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	VideoRam	64000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"KDS K22MDWB"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"KDS K22MDWB"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by alienexplorers on 2007-09-16
Try adding a modeline to you "monitor" section of xorg.conf.  It should look like this:
> Section "Monitor"
	Identifier	"KDS K22MDWB"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-85
        [COLOR="Red"]# 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
       Modeline "1600x1200_60.00"  160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync[/COLOR]
EndSection

---

### Post by mhenry35 on 2007-09-17
I spent a good week working on this, to the point that I actually reinstalled Vista just to see if the monitor really worked.  It does.

There are a few Intel widescreen issues, which we should look at seperately:

1)  Resolution isn't there (this is solved with the new Intel driver)
2)  Resolution is there, but the horizontal sync rate is wrong, causing your 1680x1050 screen to display, but leave a large black stripe on the left side, and a smaller black stripe on the right side.

Since you're using Gutsy, that means the new intel driver is already installed.  The new driver does get the 1280x800 resolution on my laptop correct, but cannot handle my 22" external widescreen (1680x1050.)

On my system, my laptop display panel is set to be OFF in the BIOS, and actually everything looked good until Gnome Desktop loaded, and the laptop panel turned back on, and I could hear the screen re-syncing, and I got the wrong horizontal refresh rate.  I know of no solution using the new driver that actually works.

The final solution:

Uninstall the new driver, reinstall the old i810 driver, install 915resolution, and do not pick a substitute graphic mode at random, overwrite the 1600x1200 mode with your correct 1680x1050 (this is mode 5a on my Intel 945GM.)  To find out what modes your system supports and their numbers, just use 

sudo 915resolution -l

Once you have 915resolution installed, create a default file for it called 915resolution, in your etc/default directory, that looks like this:

MODE=5a
XRESO=1680
YRESO=1050
BIT=32

Add the modeline (information is probably in your Xorg.0.log file) information and also the vertical and horizontal scan rates (which will be in your monitor documentation) to your Xorg.conf file.

If you're using a laptop, you'll probably have to turn off the internal panel in the BIOS.  If it stays on, it will likely not work correctly.  Don't worry, when you boot up without the external monitor, the panel will turn on by itself (at least mine did.)

I referenced a number of articles, this one is well written, but there are more out there - try a few searches on Google using Intel, widescreen, linux as your search.

[http://www.melvilletheatre.com/articles/intel-widescreen/index.html](http://www.melvilletheatre.com/articles/intel-widescreen/index.html)

Key Factors (in my opinion)
1)  Laptop panel turned off
2)  Old i810 driver
3)  915resolution
4)  Modeline in xorg.conf

---

### Post by altonbr on 2007-09-17
Thanks for all your help, but you'll laugh (or cry) about how it started working.

Gusty has this new "Screens and Graphics" dialogue that I started to play with. It seemed a little shaky as it wasn't remembering settings I put it, but when I rebooted, it implemented them.

I put in that the monitor was a generic 1440x900 LCD monitor using the i810 driver. When I rebooted, it worked and appeared properly. auto915resolution wasn't needed, and sadly, the 'intel' driver didn't work.

I'll post the X.ORG configuration once I'm back on this guy's computer.

Thanks once again.

---

### Post by mhenry35 on 2007-09-17
Well, actually that's excellent news.  I had tried downloading Gutsy Tribal 5 and using that option on the live CD, but it didn't work, so I didn't go through the install process.

I had wondered if maybe it would behave differently after a real install, but since I wasn't encouraged by the live CD, I didn't move forward.

I'll see if there's anything interesting in your xorg when you post it.

Thanks!

---

