---
title: "Wierd glitch with xscreensaver making my mouse cursor black"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by magiceraser06 on 2007-09-16
Hey guys. Im not really a beginner, been using Ubuntu for an year.  Let start by saying how awesome it is and more importantly, how AMAZING the community is for help.  Everyone should pat themselves on the back for a jolly good show.

OK, so now to business.  I FINALLY got gutsy to run perfectly on my Dell C600 laptop.  For those of you who have had the ridiculous issues with that ATI Rage Mobility 128 M3.  Just a tip for you all, all you really need to do to get it working with DRI is to:

```
sudo gedit /etc/X11/xorg.conf
```

Then, make the following changes:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	[COLOR="Blue"]HorizSync	28-70
	VertRefresh	43-60
	Option		"AgpMode" "2"
	Option		"Accel" "true"[/COLOR]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
[COLOR="Blue"]	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"[/COLOR]
	EndSubSection
EndSection
 
```
Restart and you should be in DRI mode.  No need to install any drivers or anything. Gutsy works out of the box. You will only need to make the mentioned changes and you can have resoultion.  Unfortunatly you can get DRI with resolutions above 1280x1024.  but it looks gorgeous, and thats what i use it at anyway.


Everything else works straight out with no configuration.  Now for the wierd part.

I found that my screensavers would flicker like a disco ball, but ONLY with GL screensavers.  I found on some post that it was an issue with gnome screensaver.  So I switched to xscreensaver and VOILA!!  no more flicker.. smooth rendering....so far so good.

THEN  i find that when i the screensaver runs or even when i open the panel, it runs my mouse cursor black. like the overlay is tracking my mouse.  everything else is perfect, but ONLY my mouse goes black. it will only go back to normal upon a restart of the desktop. 

Any ideas?  Im at a total loss on this one.  [

Thanks again and I'll be happy to lend a hand to anyone that needs it, concering Gutsy and the Dell C600 Latitude laptop.


cheers.




EDIT:  Here is how I fixed my cursor issue.  I edited my /usr/share/powernowd/cpufreq-detect.sh file as follow:

[CODE]# Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT  would be another way
if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
  PIII_MODULE=speedstep-ich
else
  PIII_MODULE=speedstep-smi
  [COLOR="Blue"]PIII_MODULE=speedstep_ich[/COLOR]
fi[CODE]  

The line in blue is the newly added line.  It seems to also fix my cpu_freq error I would get when running recovery mode.  hope that helps.

---

### Post by magiceraser06 on 2007-09-21
Ok, well it didn't work out so well.  My mouse cursor still goes black, but this time it takes much longer.  The screen saver has to be running for a while, or the display has to go to sleep.

I take it no one out there has had this problem?  Please, Im open to any suggestions.  it is only occuring when GL related apps are running.  

Bad driver?  I have an ATI Rage Mobillity 128 M3 Agp 2x 8mb

thanks.

---

