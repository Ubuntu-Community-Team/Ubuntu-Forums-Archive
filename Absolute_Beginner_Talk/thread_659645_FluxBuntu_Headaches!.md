---
title: "FluxBuntu Headaches!"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by 4Real on 2008-01-05
Ok Hi All!

I have a 21.6 Inch Samsung SyncMaster 216 BW Monitor!

And On FluxBuntu my screen resolutions is 1680x1050.

So I thought it was a bit strange , as usually it would be 1054 x 768 but when i set it to that the screen is WAY bigger. WTF is going on! Is it the Background is to big? Or Screen Resoltion has to be higher??? Theres no more past 1680x1050... Man , I promised my dad Fluxbuntu will be good but now this... HELP PLEASE SO I DONT GET LINUX BANNED FROM MY HOUSE!

:confused::confused::confused:
:(:(:(

---

### Post by 4Real on 2008-01-05
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


Should I Change Default Depth?
Modes???

Or WHAT? ( sorry for caps , just really nervous )

---

### Post by rkd on 2008-01-05
There are some things to try to fix resolution problems here:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I can't be sure they will help, but I think they are worth trying.

---

### Post by 4Real on 2008-01-05
meh , it's ubuntu , is it same for Fluxbuntu?

---

### Post by JoshuaRL on 2008-01-06
xorg.conf and the Xserver are the same for all the Ubuntus.  Ubuntu is a base OS with Xserver running your specified GUI.  So I would say that anything that changes your xorg.conf would work across the board.  And BTW, that is a **really** good HOWTO.

---

