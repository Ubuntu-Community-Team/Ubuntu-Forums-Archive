---
title: "iMac stuck at 512x384"
date: 2005-04-12
forum: Apple PPC Users
---

### Post by timelord726 on 2005-04-12
A freshly installed iMac (oldest kind) will not raise the screen resolution to anything higher than 512x384.  Everything else seems to work okay though.

---

### Post by heimo on 2005-04-12
Could you give some more information?

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

Copy paste *Section "Monitor"* and *Section "Screen"*. Then lookup the Driver line on *Section "Device"* and take the value on that line (for me it's nv, for you it could be vesa or vga or something else). Now type:

```
sudo xresprobe vga
```
substitute vga with the driver you're using (value from abowe, (xorg.conf->Device->Driver). Copy paste the output to your next message, it should look something like:

```
id: CM752
res: 1600x1200 1280x1024 1024x768 832x624 800x600 720x400 640x480
freq: 31-101 50-160
disptype: crt

```

The values are different, and those should reflect the monitors cababilities. Of course if you have your monitors spesification handy, you can also look there for hozizontal sync and vertical refresh rates. Or you can take lines from abowe and put them to your xconf.org's *Monitor section*. Something like this:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	31-101
	VertRefresh	60-160
EndSection

```

Be sure that Identifier is same as the Monitor line in *Screen section*.

Now, if you know what your monitor can do, for example 640x480@75Hz (edit: choose decent resolution / refreshrate), you can open another terminal window (keep xorg.conf open in gedit) and enter:
```
 gtf 640 480 75

```
Copy paste the output to your *Monitor section*.

```
  # 640x480 @ 75.00 Hz (GTF) hsync: 37.65 kHz; pclk: 30.72 MHz
  Modeline "640x480_75.00"  30.72  640 664 728 816  480 481 484 502  -HSync +Vsync

```

Watch that the hsync is in range with the HorizSync on the same section (in this example the range is 31-101 and this modelines hsync is 37.65, so we're safe). Also the VertRefresh and the refresh rate you selected (75Hz in this example) should match - in this example VertRefresh is 60-160 and modeline is 75Hz, so that's all good.

Now you can select the defaul resolution and colordepth by tweaking the *Screen section*. It should look something like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display":
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

```

Monitor name here matches the Identifier on your Monitor Section. Device line here matches the identifier on your Device section - you get the idea? :) It ties together some settings for your screen - the graphics card and your monitor. You may have more Subsections here, but only one is typically needed. Don't delete those yet, if you're not sure what your video card can do.

Just change the DefaultDepth to what you would want it to be, 16 for 65535 colors. Other valid values are 1,4,8,15 and 24. Change the Modes line to match the resolutions you want to use - the preferred one first (here it's 800x600). If that fails, it'll try for 640x480.

Check you didn't do any syntax errors, for example that Modeline needs to be on one line. Save, close other programs. (print these instructions for recovery) Hit CTRL+ALT+BACKSPACE to kill X. You might get back to X window system or login screen (gdm) with better resolution. If you don't get back, try logging in the console - change between virtual consoles with CTRL + F1 F2 F3 and so on - your X should be on F7. Try starting the X:
*startx* OR *sudo /etc/init.d/gdm start*

If that doesn't work, try fixing the xorg.conf or get back to your original by copying the backup over your changed one with:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

When you're back in X, you can cycle through different modes by pressing CTRL+ALT++ (plus sign), or go to System->Preferences->Screen Resolution.

You can do the whole X configuration process by entering:
sudo dpkg-reconfigure xserver-xorg

I'm sure I missed something, but this is slowly shaping to small HOWTO... :)

---

### Post by timelord726 on 2005-04-13
Thanks for that wonderfully in depth post, Heimo.  Unfortunately, I've now somehow managed to completely screw up my X configuration entirely.  The iMac's green light goes orange and I can't use X anymore.  My iMac is not on the internet, so here's what I got from your guide.

The *Driver* part of my xorg.conf is "ati" and apparently my iMac has a Rage 3D video card.

Running *sudo xresprobe ati* produces:
```
id: iMac
res: 800x600 640x480
freq: 60-60 75-117
disptype: crt
```

Anything else, I simply can't get at right now due to the fact that I'm locked out of X.

---

### Post by heimo on 2005-04-14
Can you get to rescue mode or console? (command line / using your Ubuntu without graphical environment)? That way you could put back the original configuration or try these in your Monitor section:
 
```
 
	HorizSync	60-60
	VertRefresh	75-117

``` 
Do you get any error messages?
 
EDIT: Use for example pico (text editor) to edit the files on console.

---

### Post by timelord726 on 2005-04-14
I am almost positive I have reset those values in xorg.conf, however I am not at my iMac right now and so cannot reproduce any error messages that may come up.  I reset the file to as close to the original as I could remember, and I still cannot get X to start up.

---

### Post by mcnelson on 2005-04-15
Good lord, a question I might be able to help with..... :) 

Super-newbie myself, but I've recently installed Hoary onto my iMac 233...had the same problem myself, managed to resolve it by ensuring the default colour depth in my xorg.conf file is set to '16' and not '24' - and then added '1024x768' to the 16 bit screen sizes bit...I'm sure you know what I mean. 

Quoth:

*Video: supports resolutions of 640 x 480, 800 x 600, and 1024 x 768 using ATI Rage IIc chip set, 2 MB provides 16-bits at maximum resolution, 24-bits at other settings, will support resolutions to 1600 x 1200 on an external monitor* 

from [here](http://www.lowendmac.com/imacs/imac.shtml).

Hope helps.

---

### Post by kpz on 2006-02-23
Thanks mcnelson. I have been searching that information for a while. I have that iMac 233 and my xorg.conf is now

```

   Section "Screen"
.....
   DefaultDepth 16
.....

   SubSection "Display"
      Depth 16
      Modes "800x600" "640x480" "1024x768"
   EndSubSection

```
And it works fine! Thanks again!

---

### Post by timelord726 on 2006-03-14
[quote=mcnelson]Good lord, a question I might be able to help with..... :) 

Super-newbie myself, but I've recently installed Hoary onto my iMac 233...had the same problem myself, managed to resolve it by ensuring the default colour depth in my xorg.conf file is set to '16' and not '24' - and then added '1024x768' to the 16 bit screen sizes bit...I'm sure you know what I mean. ...

Hope helps.[/quote] Hi there mcnelson!  Nearly a year after finally giving up the iMac for dead, you have given me what should have been a simple and obvious solution, and it actually worked!  My old iMac is once again a working computer!  Now I just need to get it hooked up to the internet and we'll have another usable computer in the house!  I really cannot thank you enough.

---

