---
title: "graphics problems - final attempt"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by keno.mentor on 2007-11-21
I have tried to fix the resolution with my S3 unichrome pro IGP gaphics chipset for some time now.  The problem is that I cannot select higher than 800x600.  In my efforts, I have tried the following:

(Kubuntu on fujitsu-siemens laptop)

1) kdesu kate /etc/x11/xorg.conf AND sudo nano /etc/x11/xorg.conf

 Both these commands give a blank text file with nothing to edit


2) sudo dpkg-reconfigure -phigh xserver-xorg

This allows me to only select the driver (vesa).  After hitting enter on "ok", the screen flickers and adjusts, comes back to the way it was but the window closes and takes me back to the terminal window i.e. not taken to the next screen where there is an option to select resolutions.

I originally used this command without the "-phigh" and was able to select the resolution but not before going through the entire configuration and selecting all the default options.  Subsequently, the whole system crashed and I could not boot kubunt.

Please someone help.  I have the feeling that this requires one simple command to fix but for a newbie it's like looking for a needle in a haystack :(

Many thanks,
keno

---

### Post by banewman on 2007-11-21
You need to install the right video card driver.
I don't use kubuntu but there should be an entry in a menu for restricted drivers - go there and see if it installs the right driver.
You need to enable all repositories to get all drivers.
Have you enabled all repositories? :)
Feel free to ask more questions. :)

---

### Post by jordanmthomas on 2007-11-21
If it helps, your file is empty because that should be a capital x in x11.
```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by daimaru on 2007-11-21
it always helps using the tabulator key in terminal to autocomplete commands or directories. that way you rule out typos. just key in the first few letters and hit tab which should auto complete your command or directory. and it saves time typing :)
if you hit tab twice you get a list of all possibilities. sometimes that might be alot. but then you get a question like 442 possibilities show them? (y/n)

---

### Post by keno.mentor on 2007-11-21
Thanks for that, I finally got to see the inside of xorg.conf!!  However...  I changed the settings to 1280x800 under "screen" and rebooted and nothing changed, the resolution is still as poor.  Should I be changing any other setting under another section?  Perhaps under "device" or anywhere else?

Many thanks,
keno

---

### Post by daimaru on 2007-11-21
could you attach your xorg.conf. would make it easier. 

Modes		"1600x1200@65"	"1600x1200@60"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"

yours should have 1280x800 in first place. nothing before it.

---

### Post by keno.mentor on 2007-11-21
This is the sections from my xorg.conf file relevant to my graphics problem

This doesn't work either.  Where to from here?

Many thanks,
keno


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200@65" "1600x1200@60" "1400x1050@60" "1280x960@75" "1280x1024@60"
	EndSubSection
EndSection

---

