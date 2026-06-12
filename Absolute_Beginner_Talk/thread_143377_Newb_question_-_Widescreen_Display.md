---
title: "Newb question - Widescreen Display"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by husky81 on 2006-03-12
I need some help getting the correct resolution working on my laptop.  This is literally day 1 with linux for me, but I'm pretty good with Windows and whatnot.  I've done some googling so I kind of know what's out there, but I'm having trouble getting the programs to fix this working.

Anyway, I have a dell 710m, that should have 1280x800 resolution.  It uses the integrated intel graphics.  I tried to use those 855resolution and 915resolution programs which is supposed to fix this, but I don't really even know the basics of how to get these programs to run.

I really need step by step directions on how to do this.  I plan on getting a ubuntu book to learn more about this, but I want to start with getting the display working.  (any suggestions for a book, by the way?)

Thanks for any help!!\\:D/

---

### Post by Klaidas on 2006-03-12
I think this should help: [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
:)

---

### Post by husky81 on 2006-03-12
Oh yeah, the only option I have when I go to System-Prefs-Screen Res- is 1024x768 at 60hz

---

### Post by husky81 on 2006-03-12
Thanks Klaidas.  That was quick!  I did try to search the forums, but I guess I wasn't looking for the right thing.  I'll let you know if I run into any problems!

---

### Post by Klaidas on 2006-03-12
No problem, I hope you'll succeed! :)

---

### Post by husky81 on 2006-03-12
I don't know... The xorg.conf file seems to have what I need already


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

---

### Post by husky81 on 2006-03-12
Haven't figured this out yet...  I went to online modeline generator, and it doesn't have the widescreen (1280x800) option.

I'm assuming there's something basic that I'm not doing...

---

### Post by shuttleworthwannabe on 2006-03-12
[QUOTE=husky81]Haven't figured this out yet...  I went to online modeline generator, and it doesn't have the widescreen (1280x800) option.

I'm assuming there's something basic that I'm not doing...[/QUOTE]

hey, I have 700m and these step-by-step instruction is what saved me a whole bunch: [http://users.skynet.be/thomasvst/linux-on-laptop/#wide](http://users.skynet.be/thomasvst/linux-on-laptop/#wide)

If it works, please send the author email.
Good luck
S

---

### Post by husky81 on 2006-03-12
Sweet.  Finally got it.  Thanks everyone!!

---

### Post by Thisbetom on 2007-03-31
Hey,

I wrote my experience down for changing it here:

[http://ubuntuforums.org/showthread.php?p=2383081](http://ubuntuforums.org/showthread.php?p=2383081)

Hope it helps! 
-Tom

---

