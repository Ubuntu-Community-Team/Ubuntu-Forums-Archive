---
title: "Screen resolution..... help..."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by night_raiders on 2007-06-26
ok i am absoultly new to linux/ubuntu so i dont know anything.... can you guys help me try to change my screen resolution to umm the one after 800x600 i can remember what it is exactly....
but can you guys help me with this.... and i tried the info on one of the threads below this and it didnt help

---

### Post by avik on 2007-06-26
The resolution after 800x600 is 1024x768, which is setup by default.  Just go to System->Preferences->Screen Resolution and change it from there.

If that doesn't work--which would be strange--let us know.

---

### Post by cogadh on 2007-06-26
You probably just have your xorg.conf configured incorrectly see [this post]("http://ubuntuforums.org/showthread.php?t=484547") for a similar problem with solution.

---

### Post by night_raiders on 2007-06-26
well i can only pick 800x600 and 740x680 on the screen resolution page.... and the link to the other thread i tried that and it already had the stuff there......

---

### Post by krul on 2007-06-26
> **night_raiders said:**
> well i can only pick 800x600 and 740x680 on the screen resolution page.... and the link to the other thread i tried that and it already had the stuff there......

You probably didn't add the screen resolutions to every color depth...review you xorg.conf and make sure you add the desired resolutions in there

---

### Post by night_raiders on 2007-06-26
I DIDNT CHANGE ANY OF THOSE \/ \/ \/ thats default




Section "Monitor"
	Identifier	"CM2019"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"CM2019"
	DefaultDepth	16
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by cogadh on 2007-06-26
Is that a Balance CM2019 19 inch LCD Monitor? If so, add this under your Monitor Identifier:
```
HorizSync    30 - 80
VertRefresh  50 - 75
```
Then logout, press CTRL-ALT-BKSPC to restart X and log back in. You should be able to increase the resolution now.

---

### Post by krul on 2007-06-26
> **night_raiders said:**
> well i can only pick 800x600 and 740x680 on the screen resolution page.... and the link to the other thread i tried that and it already had the stuff there......

You probably didn't add the screen resolutions to every color depth...review you xorg.conf and make sure you add the desired resolutions in there

---

### Post by night_raiders on 2007-06-26
i tried the code but it wouldnt let me save it says i dont have permission....

---

### Post by alienexplorers on 2007-06-26
Try adding a modeline to your xorg.conf file.

Enter gksudo gedit /etc/X11/xorg.conf

> Section "Monitor"
    Identifier     "CM2019"
    HorizSync    30 - 80
    VertRefresh  50 - 75
    Modeline       "1280x1024_65.00"  119.40  1280 1368 1504 1728  1024 1025 1028 1063 -HSync +Vsync
    Option         "DPMS"
    EndSection

Modelines can be found here:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

### Post by night_raiders on 2007-06-26
i cant save anything when i edit says i dont have permission

---

### Post by alienexplorers on 2007-06-26
are you using sudo or gksudo before your commands.  They allow you to write to almost anything.

---

### Post by night_raiders on 2007-06-26
i dont understand

like i can edit it and stuff but when i get ready to save it says i dont have permission....

---

### Post by alienexplorers on 2007-06-26
whenever you want to edit your xorg.conf file you would type in the terminal.  Enter terminal and copy the following line into the terminal.
> gksudo gedit /etc/X11/xorg.conf
when you are done editing it you just save and exit gedit.

---

### Post by night_raiders on 2007-06-26
wow thank you soo much better i have a question about limewire as well i will post the error msg that pops up in just a minute

---

### Post by alienexplorers on 2007-06-26
Good thing its working now.  Like to see people get there systems running.

---

### Post by night_raiders on 2007-06-26
it says only one software management tool is able to run at one time........ when i try to install limewire

---

### Post by alienexplorers on 2007-06-26
Not sure about this one and would hate to make you go in the wrong direction.  Try posting a brand new thread.  I'm sure more people out in forum land know more about this than me.  I could never get it running.

---

