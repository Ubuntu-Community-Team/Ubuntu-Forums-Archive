---
title: "1280 x 1024 Resolution in Feisty"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by sccrstvn93 on 2007-09-15
I cannot seem to get the resolution 1280 x 1024 in ubuntu. I have many articles on the internet but all of them are telling me differenet things. I have learned that jsut messing with xorg.conf is not ok as i have had reinstall linux 4 times. I have figured out i can back it up now tho. I installed easyubuntu and ran it as some said that would help but i still cant get the right resolution, but i can play my music now. Any help is appreciated. 
          Even if you just point me to a good guide. I have a radeon 9250 graphics card and a dell monitor that comes with the Dimension 4500. I can give you the serial number if you need it. The refresh rates are 30-70, 50-160. 
          when i run displayconfig-gtk there is a custom one and DellE772c which i guess is my monitor. When i try to set the monitors to the right resolution they dot work. Also Custom 1 is the amin monitor for some reason.

---

### Post by SOULRiDER on 2007-09-15
Open a console and type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by alienexplorers on 2007-09-15
You could try adding a modeline to your "monitor" section of xorg.conf.  You can find a modeline maker in my signature line.
Example modeline configuration:
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Generic"
    HorizSync       31.5 - 68.7
    VertRefresh     56.0 - 85.0
    Option	   "DPMS"
    [COLOR="Red"]# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync[/COLOR]
EndSection

---

### Post by sccrstvn93 on 2007-09-15
I tried: "sudo dpkg-reconfigure -phigh xserver-xorg" do i have to do anything else after? the resolution is not there. I'll try the other method.

---

### Post by sccrstvn93 on 2007-09-15
ok i tried your way alienxplorer and i now have the option of 1152 by 864. Maybe my refresh rates are screwed up? I got them from a command line but i forget which one. They are 30 -70, 50 -160. Should i try the rates in you example?

Edit: my refresh rate is now 70mhz for some reason.

---

### Post by alienexplorers on 2007-09-15
yes

---

### Post by sccrstvn93 on 2007-09-16
ok i added you refresh rates but now im back where i started and no longer have 1152 by 864. Here is what my monitor section looks like: 

Section "Monitor"
  identifier "Generic Monitor"
  modelname "Custom 1"
HorizSync 31.5 - 68.7
VertRefresh 56.0 - 85.0
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
Option "DPMS"

EndSection

---

### Post by alienexplorers on 2007-09-16
try leaving off the -HSync and -Vsync from the modeline.  Works better this way on some systems.

---

### Post by sccrstvn93 on 2007-09-16
Thx for all ur help and quick responses, but it didnt change.

---

### Post by kevdog on 2007-09-16
I really dont know if this will help, but I will post my xorg.conf file here for reference.  Backup your old config first however:

Im working on a laptop so this may be different than your case

Section "Monitor"
        Identifier      "Monitor0"
        VendorName      "Monitor Vendor"
        ModelName       "Monitor Model"
#       Option          "DPMS"
        HorizSync       28-90
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
        EndSubSection
        SubSection "Display"
                Depth           4
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "64
0x480"
        EndSubSection
EndSection

---

### Post by sccrstvn93 on 2007-09-16
i ran the autoconfig again and now have 1152 x 864 available again. Here is my xorg file: 

Section "Monitor"
	Identifier	"DELL E772c"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"DELL E772c"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Hmm i dunno wats wrong. Would manualy changing the modes work?

---

### Post by sccrstvn93 on 2007-09-16
now my monitor got an error that said "out of refresh rate"

---

### Post by Emarian on 2007-09-16
Try reinstalling drivers.

---

### Post by sccrstvn93 on 2007-09-16
how and the open source one or the regular? At first the desktop effects worked on my computer, but then i guess i installed the open source one? and they no longer work.

Edit: i have a radeon 9250

---

