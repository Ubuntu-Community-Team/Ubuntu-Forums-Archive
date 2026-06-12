---
title: "[SOLVED] Compiz, Video, and Ati driver problems"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by sneakyzor on 2008-01-06
I've been using Ubuntu 7.10 on my sony S360 laptop for the pass 3 days (first-time linux user) everything seems to be working fine, installed graphic drivers using ENVY and got compiz and normal visual effects working (although sluggisly but livable).  Now i know that it's a common problem that video play on players like VLC and Mplayer don't work when compiz is running, i was just wondering if there was work around to this.  My computer runs a ATI 9700 64mb, so i was expecting better video playback and graphics performance, but am really stumped on how to optimize my system.

here is my xorg.conf:
```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection

```

Any help would be appreciated, and although i'm quite new to linux i've learned a decent amount in the past few days, mostly thanks to reading these forums.

---

### Post by thumper13 on 2008-01-06
Just a little insight, not a solution..

When I was installing Ubuntu on my unit, I found that installing the drivers using Envy caused nothing but headaches... I'm using an ATI x200. I installed the drivers using this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

and I now have the 3d effects working, as well as for gaming.

Like I said, something to try, I'm still kind of new to this ubuntu thing too :)

---

### Post by sneakyzor on 2008-01-06
thanks,

well i did all the checks that guide gives, I have 7.12 drivers installed and working, what I'm not sure of is if its okay that my xorg.conf says that I have a Radeon 9600 (i really have 9700) and if it's at all possible to get compiz and video playback to work at the same time.  Anyone know if any of the older drivers are more stable or if they are any other tweaks I could do?

on a side note, I'm really liking linux alot, but the only thing putting me off is getting video playback working, and for some reason booting takes a really long time (4-5 mins), but the great community is def a +

---

### Post by sneakyzor on 2008-01-07
bump,

well playing around with Mplayer settings i was able to get choppy video to work by switching the video output driver to X11 (opengl), but it's still not watchable.  

Just wondering if someone can verify that there isn't much else I can do, aside from turning compiz off everytime I want to see a video.

---

### Post by sneakyzor on 2008-01-09
well I was able to solve my video woes with my ati driver.

After reading around, it was apparent the issue was with the the 7-12 ati drivers and AiGlx.  So I installed xserver-xgl through the synaptic manager, then using Envy I installed 8.40.4 drivers, restarted, and now everything works like charm.

I was even able to fix the long as boot and get the splash screen back thanks to another thread in this forum.  Now linux is running sweetly.

Just hopes this helps out anyone else also having trouble with this.

---

### Post by shareMenaPeace on 2008-01-09
Hi, just a sidenote, i tried around too with my ATI Xpress 2300 even used some guides. But the best result i got from envy with manual install

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X2300
OpenGL version string: 2.0.6958 Release

```

So i cannot remember the version but i think it was the top option.

Before this i installed restricted which is disabled but shown as "in use".


Cheers

---

