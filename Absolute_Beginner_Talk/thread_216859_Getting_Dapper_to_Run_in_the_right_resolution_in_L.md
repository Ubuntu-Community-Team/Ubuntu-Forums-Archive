---
title: "Getting Dapper to Run in the right resolution in Live form"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Over Haze on 2006-07-16
I've had my dapper drake Cd's for a few days now, so far just using it as a live CD so I can get a feel for it. The problem is cannot get it to display in the proper resolution. The resolution drop box will not drop and I have tried "Sudo dpkg-reconfigure xserver-xorg" but the changes I make never take effect. Its impossible for me to get a good feel for Ubuntu when it is displayed at a resolution lower than my screen should be displaying at all. Can anyone give me some advice?

---

### Post by Denis on 2006-07-16
You can set extra "modes" with xorg.conf: 

Edit xorg.conf (the configuration file of the X windowing system). 
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to the section "Screen"
Add the resolutions you want to the subsection with depth 24 (assuming you use 24 bit colors).

```
SubSection "Display"
		Depth		24
		Modes		**"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"**
	EndSubSection
```
You have to restart x now, press ctrl-alt-backspace. 
Can you select different resolutions now?

The changes you do will obviously be lost the next time you boot the liveCD.

---

### Post by Over Haze on 2006-07-16
Thanks I will give that a shot.

---

### Post by Over Haze on 2006-07-16
Thanks, that got her running in the right resolution. Ubuntu still wont detect my netopia usb wireless card but at least I can see Dapper Drake it its proper glory.

---

