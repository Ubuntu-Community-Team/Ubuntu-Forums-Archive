---
title: "getting new monitor to display in native resolution"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by duderduderini on 2007-05-19
Hi Guys
I just installed ubuntu aweek ago and cant seem to get the video resolution that is native to my lcd monitor. It is a Samsung Syncmaster 940N and it only is in 1024 x 768 at 60Hz,,, so being a noob I have attempted to decipher what packages, libaries etc but Its All Geek to me. I have the latest Ubuntu distro 7.04
I would appreciate some help
Thanks
Nick

---

### Post by heimo on 2007-05-19
You could try reconfiguring Xorg using these instructions:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

When dpkg-reconfigure asks about resolutions, you can manually select which ones should be available.

And welcome to Ubuntuforums! If you run into any kind of problems or questions with that advice above, don't hesitate to ask - I or someone else will try to help you through this.

---

### Post by duderduderini on 2007-05-19
Greetings from Australia and thanks for taking the time to help
Well i went to the page and typted in the following
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/xfree86/xorg.conf.md5sum'
sudo dpkg-reconfigure -plow xserver-xorg
I enter the video card it asks for then goes to the nest page about the bus id but then freezes i press enter and nothing happens..
Any ideas
I suppose being Finnish you must like rally driving.. 
From another type of racing Keke Rosberg was the best driver of his time......
Thanks
Nick

---

### Post by heimo on 2007-05-19
If dpkg-reconfigure fails, you could try ... BTW, I assume that you have already tried going to System->Preferences->Screen resolution and correct resolution isn't listed there?

Open a temirnal windows (Applications->Accessories->Terminal) and type xrandr [enter]. That should give you a list of available resolutions. Does it include 1280x1024? How about if you type
```
cat /etc/X11/xorg.conf | grep 1280x1024
```Nothing or a line with that resolution?


EDIT: And, yeah - sure, rally driving - even though I don't drive - is fantastic and I'm amazed how good they can be. Vatanen, Kankkunen, Grönholm, Mikkola, Alén... :)

---

### Post by bchaffin72 on 2007-05-19
I have fixed this problem on both my main PC and a laptop. If a reconfigure fails, you may need to manually edit the xorg.conf file in /etc/X11.

You may need to change the default color depth and add resolutions manually.
Here is a portion of my xorg.conf file:

Section "Monitor"
	Identifier	"COMPAQ 7550"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"COMPAQ 7550"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

I had to change the default color depth from 24 to 16 and add 1152X864 manually. Mine would not do over 1024X768 even though I knew it could. Try changing the default color depth and adding the resolution you need to each depth. It worked for me as a last resort.

---

### Post by duderduderini on 2007-05-21
Hi
Well i went and bought a new monitor again.. because the one they originally sold me had only analogue inputs. I have the Chimei 221D widescreen Monitor now. I have now got the specs for my radeon 9600xt.. they being
Resolutions, colors and maximum refresh rates (Hz) in 256, 65K or 16.7M colors
640x480 120 
800x600 120 
1024x768 120 
1152x864 120 
1280x1024 120 
1600x1200 85 
1920x1080* 16:9 75 
1920x1200 75 
1920x1440 75 
2048x1536 60

And for the Chimei
Output Interface&#65306;
&#12288; Pixel Pitch: 0.282 mm
Resolution: 1,680*1,050 WSXGA+
Display Color: 16.7 M (8 bits Hi-FRC)
Brightness: 330 cd/m2
Contrast Ratio: 800:1
Viewing Angle
Viewing Angle (Horizontal): 170°
Viewing Angle (Vertical): 160°
Scan Rate (Horizontal): 30 kHz ~ 82 kHz
Scan Rate (Vertical): 56 Hz ~ 76 Hz

So my question is how do i package this in xorg so that it wont go "bang"
I really appreciate the help
Regards
Nick

---

