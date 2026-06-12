---
title: "Why can I not use 1280x1024?"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by tjp.thomas on 2006-07-28
Hi there!
I know... numerous of topics covering the resolution bit. I cannot for the life of me seem to get this to work.... I have run the 

sudo dpkg-reconfigure xserver-xorg command and chosen 1280x1024 setting. When I open the xorg.conf it lists the resolutions ok, but I cannot chose the setting under System - Preferences -> Screen resolution. I still only have three options (1024/800/600). Can you help me? Below is a past of my xorg.conf file screen section?

TIA!:confused: 


Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36.2 [GeForce FX 5700]"
	Monitor		"SyncMaster 172v"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by JarG0n on 2006-07-28
I feel your pain, as I had the same problem.  If the reconfiguration of the xserver (sudo dpkg-reconfigure xserver-xorg) doesn't autodetect your monitor (hence "Generic Monitor"), then my guess is that Ubuntu utilizes a very basic display set and refresh rates that are designed for compatibility, not performance.

You've probably already seen this url, but check out the second part labeled **"Undetected Monitor Specs"**.  Once I used the "advanced" monitor config option, whereby I can input the HorizSync and VertRefresh rates, and the monitors max resolution settings, it all worked beautifully.

I hope this works for you.  Let me know.

---

### Post by JarG0n on 2006-07-28
One additional note.  In order to input the HorizSync and VertRefresh rates, you MUST know your monitors capabilities.  The document indicates googling your monitors manufacturer and model# if you don't have the manual.  I downloaded a PDF spec sheet for mine, input the specs via sudo dpkg-reconfigure xserver-xorg, and it "just worked" after that. :)

---

### Post by xrchris on 2006-07-28
Can you post the full xorg.conf file. 

Does the nvidia screen show when you bootup?

---

### Post by Indras on 2006-07-28
I have an IBM-9495 17" LCD monitor, and with every version of linux I've ever tried to use, the "Generic Monitor" settings never allow me to use 1280x1024.  That's because the refresh rates that it defaults too aren't correct for my monitor.

Look on the back/side of your monitor for the exact model number and drop it in google.  Most manufacturers will release an html or pdf file with all of the exact specs, including refresh rates and resolutions.  Then go to your xorg.conf file and pop in the values manually, save the file, and restart.  That should fix your problem.

---

### Post by britgamer on 2006-07-28
Hello which driver are you using? The open source nv or the official Nvidia driver?

I had a similar problem with my monitor, a HDTV with a resolution of 1360x768. Changing refresh rates etc didn't work for me and I actually gave up. But later on when I installed the official driver it worked perfectly.

If you are using the nv driver installing the nvidia ones *may* work and save you some hassle too

---

### Post by tjp.thomas on 2006-07-28
THANKS FOR THE INPUT GUYS! I will google for my monitor, when I get back home... 

JarG0n: I will try and locate the info on my SyncMaster 17 monitor!
xrchris: I do get the nvidia screen when booting. I will post the entire file sometime tomorrow... ;)
Britgamer: When I install using the sudo dpkg-reconfigure xserver-xorg option I select Nvidia and it finds my 5700 fx card automatically. Should I try and install the official driver from nvidia.com?

Have a nice day!

---

