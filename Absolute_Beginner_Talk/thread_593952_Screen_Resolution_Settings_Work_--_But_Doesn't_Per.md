---
title: "Screen Resolution Settings Work -- But Doesn't Persist Thru Logout/Restart"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by thornomad on 2007-10-27
Hi -

Fresh install of Gutsy today.  Ubuntu is defaulting to 1280x768 resolution.  I open System --> Admin --> Screens & Graphics and change the resolution to 1024x768.  Works beautifully.  Nice image.

However, if I restart or logout, Ubuntu reverts back to 1280x768 (which is stretched and not very pleasant to look at).  I have tried running: "sudo dpkg-reconfigure -phigh xserver-xorg" and selecting only 1024x768 -- this killed X and I had to revert to an older /etc/xorg.conf.

I have also tried manually editing /etc/xorg.conf and removing all mention of any resolution other than my preferred one and that doesn't work.  

Anyone know how I make the settings I choose from "Screens & Graphics" persist?  Any ideas ?

Thanks,
Damon

xorg.conf and screen image attached.

---

### Post by keyboardashtray on 2007-10-28
> **thornomad said:**
> Hi -

Fresh install of Gutsy today.  Ubuntu is defaulting to 1280x768 resolution.  I open System --> Admin --> Screens & Graphics and change the resolution to 1024x768.  Works beautifully.  Nice image.

However, if I restart or logout, Ubuntu reverts back to 1280x768 (which is stretched and not very pleasant to look at).  I have tried running: "sudo dpkg-reconfigure -phigh xserver-xorg" and selecting only 1024x768 -- this killed X and I had to revert to an older /etc/xorg.conf.

I have also tried manually editing /etc/xorg.conf and removing all mention of any resolution other than my preferred one and that doesn't work.  

Anyone know how I make the settings I choose from "Screens & Graphics" persist?  Any ideas ?

Thanks,
Damon

xorg.conf and screen image attached.

Hi - I know I might be way off, but did you already try System>Preferences>Screen Resolution and checking the "Make default for this computer" checkbox?

I was all in a tizzy about it reverting and all along I just didn't notice that preference option. :oops:

---

### Post by daimaru on 2007-10-28
if you want to reconfigure your xserver you have to use
```
sudo dpkg-reconfigure xserver-xorg
```
it will ask you for everything from video driver to keyboard layout, but you can choose most of the default values. you can also set up your resolution and if you got your keyboard settings wrong after creating the file just open your old xorg.conf and the new one, copy paste all the old stuff over replacing keyboard mouse stuff just not the video stuff. 

that should work maybe it would be easier just editing my hand cause your section about resolution looks kinda weird to me here's my monitor etc section of xorg.conf

```
Section "Monitor"
	Identifier	"Samsung SyncMaster 214T"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Samsung SyncMaster 214T"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

```

so my system defaults to the first resolution in the Modes line (1600x1200)

---

### Post by daimaru on 2007-10-28
oh i just missed the part in your xorg.conf file where it says**[COLOR="Red"] virtual 1600x1200[/COLOR]**
you have your desktop set up so it emulates 1600x1200 just [COLOR="Red"]delete that line[/COLOR] and you should be fine. you can do that in a gui somewhere too probably under the resoutions thingi but its faster just to edit xorg.conf

---

### Post by thornomad on 2007-10-28
> **keyboardashtray said:**
> Hi - I know I might be way off, but did you already try System>Preferences>Screen Resolution and checking the "Make default for this computer" checkbox?

I was all in a tizzy about it reverting and all along I just didn't notice that preference option. :oops:

Oh wow -- I didn't even notice that GUI option ... I was stuck on using the System->Admin->Screens & Graphics.  Geez ... 

The computer in question isn't with me any more ... but I'm going to try and get its owner to give that a shot and see if it makes a difference.

Thanks,
Damon

---

### Post by thornomad on 2007-10-28
> **daimaru said:**
> oh i just missed the part in your xorg.conf file where it says virtual 1600x1200
you have your desktop set up so it emulates 1600x1200 just delete that line and you should be fine. you can do that in a gui somewhere too probably under the resoutions thingi but its faster just to edit xorg.conf

All right, I will give a simpler xorg.conf a try too (if the GUI modification doesn't work).  I did try removing the "virtual" line once but that didn't seem to make a difference.  I also removed all the other lines and that hadn't changed it either.  Maybe something was stuck somewhere that I overlooked.  Will take another go-round at it.

Thanks,
Damon

---

