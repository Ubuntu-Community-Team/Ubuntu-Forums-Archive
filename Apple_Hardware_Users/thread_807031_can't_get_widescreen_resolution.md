---
title: "can't get widescreen resolution"
date: 2008-05-25
forum: Apple Hardware Users
---

### Post by ciclopropano on 2008-05-25
I have an intel mac 20'', with a native resolution of 1680x1050 running xubuntu gusty gibbon.
when I try to change the resolution using xrandr, it tells me that the highest possible is 1400x1050. when I open the xorg.conf file I cant find any place where I can set all the possible resolutions:

[PHP]Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection
EndSection[/PHP]

by the way, this xorg.conf file has been modified by envy when I installed the ati driver, I couldnt get the right resolution before anyway. (will it solve my problems if I update to hardy heron? a friend told me it was better for the mac to stick up with gusty

---

### Post by cyberdork33 on 2008-05-25
I have a 20" iMac as well and Hardy works great. I don't know why you are having an issue with the resolution though. Works without issue for me.

You can try commenting out the HorizSync and VertRefresh lines and restart to see if it allows the higher resolution.

---

### Post by ciclopropano on 2008-05-25
I did so, and now its telling me the 1400x1050 is the only resolution available

---

### Post by Brightbelt on 2008-05-25
Not to discount your problem, but I have a 24" iMac, and I get a good screen 
resolution running Hardy. It might be worth considering upgrading. 
But that is clearly your decision.

Good Luck,...Frank B.

---

### Post by ciclopropano on 2008-05-25
thanks for the advice, I upgraded already and I got the right resolution now. :popcorn:

---

