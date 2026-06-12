---
title: "Logon Screen Using Wrong Screen Resolution"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by AlistairH on 2008-02-10
I'm having a problem trying to get my logon screen to use the correct resolution.

I'm using a 19" widescreen LCD with a resolution of 1440 x 900 yet the logon screen appear to be using something different (smaller) from this. Although all the elements of the logon screen are visible, the boxes and fonts are really big. In addition, the fonts are not smooth.

I've edited my xorg.conf file as outlined in other posts and I've included the pertinent section below but it hasn't helped. The problem is present, irrespective of which logon them I choose.

```
Section "Monitor"
	Identifier	"TS902W"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0 - 65.0
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"TS902W"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1440	900
		Modes	"1440x900@60"
	EndSubSection
EndSection
```

Any other suggestions would be appreciated

---

### Post by philinux on 2008-02-10
Install then run startupmanager from synaptic. It's menu item ends up in sys>admin.

Select the res you want for the startup screen.

---

### Post by AlistairH on 2008-02-11
Hi Phil

I'm afraid the startupmanager didn't do anything for me. Though having used it I don't see why it would as it, as far as I can make out, changes settings for the boot process but its the gdm login window that's causing the problem after the boot process has finished.

When I've got time I'll take a look at my other Ubuntu box which shares the same monitor through a KVM switch but doesn't exhibit the problem though it does have a different hardware spec.

---

### Post by AlistairH on 2008-02-13
Well, I cannot see anything obvious between the xorg.conf file on the pc with the problem compared to the one without the problem - other than they use different graphics cards and drivers. The problem machine is using Intel drivers and the 'good' machine is using SiS.

Both machines display perfectly well and as they should once I'm fully logged on.

I'll play around with xorg a bit more but I'm open to any suggestions.

---

### Post by dca on 2008-02-13
I always thought gdm login took it's setting from 'X'...  I don't know if this will help or not...
 
[http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

---

### Post by AlistairH on 2008-02-13
Thanks for responding dca.

Unfortunately I've already tried the suggestions mentioned in the link you posted but to no avail.

I've stripped out from xorg.conf all reference to any screen resolution other than my monitor's native resolution of 1440 x 900 - no effect. As the GDM login screen behaves itself on my other Ubuntu box using the same monitor, I can only assume that the problem lies with the graphics drivers/card.

The problem machine, a Dell GX260, has an Intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device and Ubuntu insists on using the Intel Experimental Mode Setting Driver. I've tried changing to the Intel driver for the i810 series, which covers the 845G chip set but whenever I restart X I get the same problem and on checking via the Screens and Graphics applet I find it's back to the experimental driver.

This seems to have been a common problem with Ubuntu 7.10 but unfortunately for me, all the solutions that I've come across have not helped in my case. Once I'm logged in the desktop is fine. It's just one of the little niggles that I'll have to learn to life with it seems.

---

### Post by AlistairH on 2008-02-14
This just gets more and more bizarre...

Having given up trying to sort this and reluctantly accept my login screen displaying at 1280x768 with it's blurry text rather than the native 1440x900 I want, I just switched on only to find my desktop had decided to resort to 1280x768 as well!

I checked my xorg.conf file just to confirm that no changes had been made which there hadn't. The only screen resolution referenced in that file is 1440x900. So where does X/Gnome get 1280x768 from?

I had to reset my defaults using the Screen and Graphics applet and did a quick CTRL+ALT+BACKSPACE and I'm back to where I was originally with a 1280x768 login and a 1440x900 desktop.

X is clearly getting the 1280x768 from somewhere, but where?

---

### Post by kainalu on 2008-04-25
seconding this. supposed to be 1280x1024, at 640x480

---

### Post by ninjabob7 on 2008-04-26
I've got a similar problem, except the gdm screen is too big for the physical screen and the bottom-right area is cut off. Once I'm in xfce, it's fine.

---

### Post by GandalfTheNerd on 2008-04-28
I had this problem, but it went away when I edited xorg.conf so that the first entry in the "modes" line matches the resolution given in the "Virtual" entry.  For example, I have:

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"Iiyama VisionMasterPro510"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1600x1200@60"	"1280x1024@60"	<other modes removed for brevity>
	EndSubSection
EndSection

I seem to remember this problem first arose after I installed the nvidia drivers.  Entire xorg.conf is attached if anyone is interested.

---

### Post by petaskeeta on 2008-05-01
I'm having the same problem as well.

I have a 17" CRT and the login screen is using 1440x900, which completely warps the screen and stresses out the monitor.

The login screen's default res was 1440x900 and the desktop was 1280x1024.

I don't know why the res for the login is so high. It should be something low for CRT's. Both of them should be low by default. If my monitor can't display the res its not going to show anything.

---

### Post by mwshook on 2008-05-02
Fixed it!

I used DCA's suggestion: (thanks)
[http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

GDM (the logon program) gets takes it's resolution from whatever is listed first in your xorg.conf
Then, after you log on, Ubuntu changes the resolution to the one the user asked for.

You need to fix the "Screen" section of xorg.conf.
This is what mine used to be:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"800x600@60"	"832x624@75"	"800x600@85"	"1024x768@85"	"800x600@75"	"1024x768@75"	"800x600@72"	"1024x768@70"	"800x600@56"	"1024x768@60"	"640x480@85"	"1024x768@43"	"640x480@75"	"1152x864@75"	"640x480@72"	"1280x1024@75"	"640x480@60"	"1280x960@60"	"1280x960@85"	"1280x1024@85"	"1280x1024@60"	"1280x960@75"
```

"Virtual" is the size of the desktop (huge), and the screen resolution the logon screen uses is whatever is listed first under "Modes" 

So I changed the section to this:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
Monitor         "Configured Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1024    768
                Modes           "1024x768@75"   "800x600@60"    "832x624@75"    "800x600@85"    "1024x768@85"   "800x600@75"    "800x600@72"    "1024x768@70"   "800x600@56"    "1024x768@60"   "640x480@85"    "1024x768@43"   "640x480@75"    "1152x864@75"   "640x480@72"    "1280x1024@75"  "640x480@60"    "1280x960@60"   "1280x960@85"   "1280x1024@85"  "1280x1024@60"  "1280x960@75"
#       "1400x1050@60"  "1400x1050@75"  "1600x1200@65"  "1600x1200@60"  "1600x1200@75"  "1600x1200@70"  "1792x1344@60"  "1856x1392@60"  "1920x1440@60"  "2048x1536@60"


```

So now my logon screen has a 1024x768 desktop, and my monitor is set at 1024x768

To summarize, put the resolution you want first in the "Modes" list. Then make sure "Virtual" is the same resolution.

**Someday** I'll be able to install Linux without mucking around in xorg.conf.

---

### Post by airencracken on 2008-05-03
> **ninjabob7 said:**
> I've got a similar problem, except the gdm screen is too big for the physical screen and the bottom-right area is cut off. Once I'm in xfce, it's fine.

Yup I'm having the same problem. Except I'm using GNOME.

---

