---
title: "HP NC6320 Native Resolution"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by jezster on 2007-01-03
Hello All,

I have recently installed Ubuntu 6.10 on my HP NC6320 laptop.  Everything works really well except for the screen resolution which seems locked at 1280x1024, however the native resolution is 1400x1050.  I have tried editing many of the options within the xorg.conf file but with no luck.  

Has anyone managed to get native resolution working?  I have inserted my config file as  a guide...

```
Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	50-180
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

```

Many Thanks,

Jez

---

### Post by alienexplorers on 2007-01-05
Try using this line in your xorg.conf file:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	50-180
        Modeline "1400x1050_75.00"  155.85  1400 1496 1648 1896  1050 1051 1054 1096  -HSync +Vsync
EndSection

---

### Post by nilicule on 2007-01-08
> **alienexplorers said:**
> Try using this line in your xorg.conf file:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	50-180
        Modeline "1400x1050_75.00"  155.85  1400 1496 1648 1896  1050 1051 1054 1096  -HSync +Vsync
EndSection

For me this doesn't work, I'm still not getting any other resolution than 1024x768 when I use the configuration as defined below.

```
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

```

---

### Post by simonbowen on 2007-06-14
Hey

I am not sure whether you even managed to fix this problem. 

I managed to get 1400x1050 on my NC6320 running feisty by running

```
sudo apt-get install 915resolution

```

Hope this helps someone, I spent the last 3 hours trying to get this to work!

---

### Post by smoothcne on 2008-02-28
> **simonbowen said:**
> Hey

I am not sure whether you even managed to fix this problem. 

I managed to get 1400x1050 on my NC6320 running feisty by running

```
sudo apt-get install 915resolution

```

Hope this helps someone, I spent the last 3 hours trying to get this to work!

Would you mind posting your xorg.conf file after you ran this, I tried it and never got any changes applied to mine. ???? 

J

---

