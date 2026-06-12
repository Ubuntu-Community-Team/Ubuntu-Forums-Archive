---
title: "[SOLVED] the screen area is larger than my monitor"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by energy. on 2008-04-01
I did a fresh install of 7.10 last night.  I installed the nvidia proprietary driver and have two monitors connected to my video card.  Twinview seems to be working fine and I'm able to drag windows from one monitor to the other.  However, the area of each desktop is larger than the size of the monitors.  To see the toolbars I have to cursor off screen and the desktop "pans" to see what's hiding there.  

I'm a complete beginner.  Can anyone guide me through resolving this?

---

### Post by energy. on 2008-04-01
any help?

---

### Post by forrestcupp on 2008-04-01
Did you try running **nvidia-settings** and mess with the resolution and refresh rates.  It sounds like maybe a refresh rate thing.  Try that and reboot if need be, to see if there are changes.

---

### Post by Mogurijin on 2008-04-01
The problem is in resolutions. You can try System -> Preferences -> Screen Resolution and setting the appropriate resolution for you monitors :D.

---

### Post by energy. on 2008-04-01
> **forrestcupp said:**
> Did you try running **nvidia-settings** and mess with the resolution and refresh rates.  It sounds like maybe a refresh rate thing.  Try that and reboot if need be, to see if there are changes.

the screen resolutions are set to 1280x1024 which is the native resolution of my lcds.  however, I noticed that it says that the resolution of X screen is 3200x1200.  It seems that this is what I need to adjust.  By my guess this should be set to 2560x1024.  How do I change this?

---

### Post by energy. on 2008-04-01
I think we're close to resolving this one

---

### Post by forrestcupp on 2008-04-01
Try this.  Open your nvidia-settings and click on 'X Server Display Configuration'.  At the bottom right, click the Advanced button.  That gives you a text box called 'Panning' that you can enter the size you want for panning.  Maybe that's what you need.

---

### Post by energy. on 2008-04-01
> **forrestcupp said:**
> Try this.  Open your nvidia-settings and click on 'X Server Display Configuration'.  At the bottom right, click the Advanced button.  That gives you a text box called 'Panning' that you can enter the size you want for panning.  Maybe that's what you need.

I've resolved the issue.  I opened up the xorg.conf and started poking around in there. 

```
Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"CRT-1: 1280x1024_60 +0+0"
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
```

the line that says "virtual 1600   1200" has been changed to "virtual 1280  1024"

---

### Post by forrestcupp on 2008-04-02
Thanks for posting your solution for future reference.

---

