---
title: "installing drivers (and getting ati 7000 to work)"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by turbo63 on 2006-01-07
Ok, I got everything to work, but I can't stand this 800*640 resolution.  I have a ATI Radeon 7000.  I can't find a driver and don't know how to install them.  (haveing trouble installing my lexmark 7200 printer driver).  Any ideas out there?  I see a bunch of articles on the 7000 but all of them are way above my head.  I just want the resolution to be 1024*768 and I would be happy.

Thanks!
Kevin

---

### Post by loupy on 2006-01-07
in your xorg.conf located in /etc/X11 is "ati" the selected driver?  It may be set to "vesa" which may be causing the problems. If it is "ati" already you can try adding the "1024x768" resolution manually and see if that works.  I have a 9700 so I can't you help much beyond that.

---

### Post by poofyhairguy on 2006-01-07
Write this command down:

>  sudo dpkg-reconfigure xserver-xorg

Then boot into recovery mode and use it.

---

### Post by turbo63 on 2006-01-07
Here is what my xorg.conf files says?  seems like it is correct.  Why can't i change my resolution in "screen resolution" under "preferences"?

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by turbo63 on 2006-01-08
poofyhair guy.  The above is after I did what you said.

---

### Post by poofyhairguy on 2006-01-08
The problem is that your monitor is not setup correctly. The video card is set up fine.

What kind of monitor is it? Any info?

Using that command I gave you at the end if you pick the harder mode and answer some questions about your monitor it WILL work.

I can help you get that info if I know what kind of monitor it is.

---

### Post by turbo63 on 2006-01-08
wow thanks for all the help.  The monitor is pretty genric.  it says I 7sp on it.  It is a generic 17" CRT.  Pretty cheap.  Can I just manually put somthing it.  I have windows XP installed as well and it works fine on that.  I could get that driver info if it would help.

Thanks!
Kevin

I really like the OS so far.  If it was at a higher rez it would be great.  Sorry to keep brothering you with all these questions.  I am pretty tech savy but first time on linux and it is like a whole new world.

---

### Post by turbo63 on 2006-01-08
When I type in the sudo dpkg-reconfigure xserve-xorg no prompts come up.  it just list a bunch of things.  I am lost in the linux command line world.

Thanks!
Kevin

---

### Post by turbo63 on 2006-01-09
I figured it out.  I had to stop gnome first and then restart it after I was done

Thanks everybody

---

