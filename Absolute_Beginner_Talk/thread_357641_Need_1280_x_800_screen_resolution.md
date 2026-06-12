---
title: "Need 1280 x 800 screen resolution"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by havedampton on 2007-02-09
I have a HP Pavilion dv6253cl, AMD Turion 64, nVidia GeForce Go 6150 graphics card

Running 6.06

There is no option for the correct screen resolution of 1280 x 800 in the drop down menu under screen resolution.

Please help...I'm all squished.

---

### Post by jpeddicord on 2007-02-09
Open up a terminal window, and type `sudo gedit /etc/X11/xorg.conf`. This should open up an editor window. Scroll down until you see **Section "Screen"** in the file, along with a list of resolutions. For each subsection, add "1280x800" to the end of each line (with quotes and a space before).

Save the file, and then it's time to restart X. Press Ctrl+Alt+Backspace, and the screen will go blank. Within about 10 seconds, the login window will reappear. Login, and then you should be able to properly set your screen resolution from System > Preferences > Screen Resolution.

Jacob

---

### Post by Happy_Man on 2007-02-09
run the following code in your terminal:

```

dpkg-reconfigure xserver-xorg

```

That reconfigures your display settings via the terminal GUI. Just go through and answer all the questions, and if you did it right, you should have your resolution!

EDIT:
Ah, jacob's is more to the point. If that works for you, great! I've had problems manually editing /etc/X11/xorg.conf, and if it messes up X even more, run the code above. That's the last resort fix for most any display problem. Just a tip!

---

### Post by vigleik on 2007-02-09
Before you edit your xorg.conf file, do yourself a favor and make a backup copy. (You never know.)

Another method is to type "sudo dpkg-reconfigure xserver-xorg" and follow the directions. At some point you'll get a choice of screen resolutions.

---

### Post by havedampton on 2007-02-09
I've done both suggestions now, and I still can't select 1280x800 in the system preferences.

I restarted so I'm sure this is actually the saved file:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Like I said, I also did the dpkg-config and added 1280x800.  Also didn't work.

suggestions?

---

### Post by Happy_Man on 2007-02-09
I know this may sound like an insult, but I have to ask whether you really selected it in dpkg-config by highlighting the choice and pressing spacebar. I remember way back when when I messed up xorg.conf by mistake and spent two days ranting at my screen because I didn't know how to select resolutions. Just a way of eliminating possibilites, you see.

---

### Post by havedampton on 2007-02-09
ok, I went through the GUI and removed the smallest resolution and checked the 1280x800

I KNOW I DID IT

when I look at the file now, after restarting and logged on as root, it now looks like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
EndSection


when I look at the screen resolution preferences now, it still is giving me the ORIGINAL three choices.

????

suggestions?

---

### Post by Happy_Man on 2007-02-09
When you say restart, do you mean restart X or restart the computer?

---

### Post by mekkah on 2007-02-09
Use the Synaptic Package Manager to obtain a package called ”**xresprobe**” (X Resolution Probe). Then reboot & you should be able to change it without any fuss :KS 

"X Resolution Probe
xresprobe is a package that probes both laptop and DDC-compliant screens for
their standard resolutions, and returns a specifically-formatted, easy-to-parse
output.

It contains the 'ddcprobe' package, which performs a DDC probe to the monitor;
however, ddcprobe only works on i386 and powerpc. The laptop detection routines
are, however, sufficiently generic to to be useful to other architectures."

---

### Post by havedampton on 2007-02-09
I've tried both kinds of restarts.  Both with no success.

---

### Post by havedampton on 2007-02-09
I have no idea what the Synaptic Package Manager is.

It sounds a little scary- probing

---

### Post by vigleik on 2007-02-10
Which graphics driver are you using? Since you have a fairly good Nvidia card it would help you a lot to use the nvidia driver.  Maybe that'll allow you to get the right resolution. I always have to install the nvidia driver first, before I can get the correct resolution for my monitor.

Search the forum for how to install the nivida driver, you'll find many howtos. Or install easyubuntu.

---

### Post by miker2069 on 2007-06-09
Just to add to the knowledge base on this I had a similar problem with a Dell Dimension 3000 (the integrated intel graphics card Intel Extreme Graphics 2 and a Dell 1900FP monitor.  Ubuntu 7.0.4 installed fine, but I could only get a max of 1024X768.  It seems to have detected the graphics card correctly but came up with Generic Monitor (I hear this is an issue that happens a lot).  I had to match the 1900FP frequency exactly in the /etc/X11/xorg.conf file exactly with my monitor (to solve the hsync out of range problem), then add the display mode of 1280X1024.  Which I did,  what threw me was that I needed to add it as 1280x1024 (lowercase x) , it all worked after a CTRL-ALT-backspace to restart the X server.  

Hope this helps someone else.

---

