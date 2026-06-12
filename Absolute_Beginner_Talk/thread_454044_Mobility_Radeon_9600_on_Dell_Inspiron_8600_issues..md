---
title: "Mobility Radeon 9600 on Dell Inspiron 8600 issues..."
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by twinight on 2007-05-25
I am a complete novice; be gentle.  Any hand-holding is gladly appreciated.

Basically, everything seems to be working well, wireless, etc, out of the box.  Just currently playing around with things, and realized that my resolution was very low (1024x768).  Tried to up it to my default native res of 1920x1200 and that did not work at all, so I figured it was due to not having the ATI drivers installed.

I went to restricted device management, grabbed the "ATI Accelerated graphics driver" that was available there, and it downloaded, prompted for a reboot, and that went smoothly... problem is it is ALSO running me at 1024x768, and in addition, the option to go higher than that is not even present on the dropdown box.  (yes, I'm only using the GUI so far... I have no idea how to edit anything manually yet!)

So I went and checked Restricted Drivers again, and now the "enabled" box is checked next to the ATI driver, but the status is "Not in use."  I would assume this is the issue, but, I really have no idea how to fix it at all.

Any help would be greatly appreciated!

Thanks!

---

### Post by twinight on 2007-05-25
Hooray!  A little bit more google to the rescue, I think!

I found some information specific to the 8600 [right here.]("http://blog.dreamdevil.com/index.php/2007/04/22/installing_ubuntu_feisty_inspiron_8600")  I just followed the directions and manually added the resolution to xorg.conf.

Now, part of the question still stands though.  Should I be worried that the status is still "not in use?"

Thanks!

PS:  Unrelated, but, if anybody else with Inspiron 8600 problems read this, maybe this'll apply for you too.  For me, the trackpad was very, VERY sluggish, and changing mouse speed etc didn't fix it, but I found a site that mentioned yet more xorg.conf alterations to add some values to change it.  I just tweaked it and restarted x repeatedly (is there a faster way to do this without restarting x?).  Information can be found [here.]("http://vincel.livejournal.com/146789.html")

---

### Post by twinight on 2007-05-25
Ok, at the behest of a friend who suggested I run fglrxinfo, I get the following:

xlib: extension "glx" missing on display ":0.0".
xlib: extension "glx" missing on display ":0.0".
error: couldn't find rgb glx visual!

It is, apparently, not quite working.  :(  At least the 3d acceleration stuff isn't.

Any help at all would be greatly appreciated!  Again, total novice here.

Thanks so much -- I'm really enjoying my time with the OS, even with the bumps and such.  It's a wonderful change of pace.  It's fun learning again!

---

### Post by twinight on 2007-05-25
I attempted to follow [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") step by step in order to do a manual install, but the last steps resulted in a core dump.

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

I restored the xorg.conf and attempted to manually do the first step there as suggested, but then the second resulted in a similar (if not same) core dump.

Now, of course, I've mucked around to the point where the restricted device manager is telling me I don't have any restricted devices, and I'll probably have to just reinstall to get back to square one.  Which is alright -- I didn't really DO anything yet, wanted to wait to get it all setup first.

But, still... I'm at a complete loss now.  Please help?

Thanks.

---

### Post by twinight on 2007-05-25
Nevermind -- I'll move this to tech support, upon scouring around and given the complexity of my questions, I think I've moved into regular tech support land.

Thank you!

---

### Post by Tavorisch on 2007-11-08
Dear Sir, I have been dual booting ubuntu 7.04 tried gutsy but no luck with some certain parts of madwifi! back to fesity again, and have direct rendering and 1680x1050 res going.. althouhg a little flaky with 1 thing, which is the fade effect (asking you for your keyring)  im guessing its the refresh rate i have it set at that is doing this but, cube effect and wobbly windows works great..
what i did was, I kept the default video drivers when you install feisty, i did install ```
sudo apt-get install xserver-xgl
``` although Im not sure if that has anything to do with it.. So if you do have the restricted drivers in the restricted drivers manager, uncheck that.. go into your xorg.conf ```
sudo gedit /etc/X11/xorg.conf
``` make sure your extensions section on the bottom says this,
```
 Section "Extensions"
Option "Composite" "disable"
EndSection
```
if not change it to that!,, now go to your screen sections and add in your resolution! mine looks like this ```

        Section "Screen"
	Identifier	"Default Screen"
	Device		"                                      "
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

``` save and close! restart X(video and desktop part of your linux by,,   Ctrl+Alt+Backspace... login see if that worked.. 
I realize your resolution is a bit higher than mine just put whateer ur max is in there.
if that doesn't work i would try the ```
sudo dpkg-reconfigure xserver-xorg
```
command.. hope this helps sir! it got me to the point where I am happy with my inspiron 8600 running linux with that pain in the *** 9600 mobility

---

