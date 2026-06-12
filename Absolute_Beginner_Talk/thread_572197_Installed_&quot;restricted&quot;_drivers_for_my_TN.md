---
title: "Installed &quot;restricted&quot; drivers for my TNT2 Card - Res too low. No option to change."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by 1Frothy on 2007-10-10
I installed restricted drivers for my TNT2 based video card. Now the resolution is no longer 1680x1050 but maximum of 800x600. I just can't find an option to change it. Please help,

---

### Post by overdrank on 2007-10-10
> **1Frothy said:**
> I installed restricted drivers for my TNT2 based video card. Now the resolution is no longer 1680x1050 but maximum of 800x600. I just can't find an option to change it. Please help,

Hi and welcome, This link should help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Good luck!

---

### Post by 1Frothy on 2007-10-10
Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1680x1050"     "1280x1024"     "1280x960"     $
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1680x1050"     "1280x1024"     "1280x960"     $
        EndSubSection
        SubSection "Display"
---

Seems right I thought. But still not higher resolution is available for me. :(

---

### Post by overdrank on 2007-10-10
> **1Frothy said:**
> Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro]"
        Monitor         "SyncMaster"
        [COLOR="Red"]Defaultdepth    24[/COLOR]
        SubSection "Display"
                Depth   1
                Modes           "1680x1050"     "1280x1024"     "1280x960"     $
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1680x1050"     "1280x1024"     "1280x960"     $
        EndSubSection
        SubSection "Display"
---

Seems right I thought. But still not higher resolution is available for me. :(

Hi and there has been mention to change the default depth to 16 has helped some. Good luck!

---

### Post by ravenwere on 2007-10-10
You also could include the specifications of your monitor which will change your options eg. see my /etc/X11/xorg.conf file

```
Section "Monitor"
	Identifier	"ADI V95F"
	Option		"DPMS"
	Horizsync	30-95
	Vertrefresh	50-200
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
	Monitor		"ADI V95F"
	Defaultdepth	24
	SubSection "Display"
		      Modes		"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"
	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

```

I got lazy editing this file and only include my default depth now. You have to find the specs (Horizsync and VertRefresh) of your model of monitor from manufacturer documentation or on the "net".

---

### Post by 1Frothy on 2007-10-10
> **ravenwere said:**
> You also could include the specifications of your monitor which will change your options eg. see my /etc/X11/xorg.conf file

```
Section "Monitor"
	Identifier	"ADI V95F"
	Option		"DPMS"
	Horizsync	30-95
	Vertrefresh	50-200
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
	Monitor		"ADI V95F"
	Defaultdepth	24
	SubSection "Display"
		      Modes		"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"
	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

```

I got lazy editing this file and only include my default depth now. You have to find the specs (Horizsync and VertRefresh) of your model of monitor from manufacturer documentation or on the "net".

:KS Thanks for your help! I got my settings from the Samsung site so...

Horizsync	30-81
Vertrefresh	56-75

I'll try them when I get home tonight!

---

### Post by ravenwere on 2007-10-10
Let us know how you go. That Vertrefresh rate looks low.

---

### Post by ravenwere on 2007-10-10
Disregard that last load of **** I assumed you were running a CRT monitor with a TNT2 card. From the settings it looks like you're running an LCD Syncmaster. I just happen to have a 940BW on the other computer. It is dual boot with windows and kubuntu 7.04. The optimum monitor resolution is 1440x900 for the 940BW according to Samsung. I will post my xorg.conf file for you.

Looking back to your original post I assume you were running the 1680x1050 on the unrestricted drivers with ubuntu 7.04 feisty?

I am also assuming you have a subsection "Display" listing the modes for depth 16 and depth 24???

I would agree with Overdrank that given the age of this card you will prob. get more options with a defaultdepth of 16.

My other thought is that (correct me pls those who know) the restricted drivers are used to access the 3D functionality of the the cards and given that the TNT2 cards had only 32M or so of onboard RAM these drivers may lower performance??!? not sure.

---

### Post by ravenwere on 2007-10-10
Sorry 1Frothy, checked the other PC. I must have reinstalled kubuntu on it at some stage so the xorg.conf is standard (1024x768) with no options to go higher.

What I did to change it before was download Envy (an application written by one of the community to install the latest nvidia and ati drivers) then I allow it to overwrite my xorg.conf but it usually stuffs something up so I end up tidying it up manually.

However, seeing gutsy is out in a few days, and I'm not sure we'll need Envy to update the drivers, I would suggest you wait and upgrade to gutsy before doing any more. Let me know how you go.

Regards,

---

### Post by captainkernelpanic on 2007-10-10
after you go into restricted modules and make sure that enable box is checked... run

sudo dpkg-reconfigure xserver-xorg

make sure that nvidia drivers are selected.. not nv. onward and upward. 
worked 4 me...

---

### Post by callan79 on 2007-10-11
> **1Frothy said:**
> I installed restricted drivers for my TNT2 based video card. Now the resolution is no longer 1680x1050 but maximum of 800x600. I just can't find an option to change it. Please help,

Hi,

I had this same issue a few weeks ago, and I found a solution that works. Lucky I wrote the solution on [my website](http://flog.cruzn.net.au) as I knew it would come in handy!

First go to Terminal and run the command ```
gtf 1440 900 75
``` - note this is for 1440x900 resolution, 75Hz refresh, so substitute appropriate value for the monitor

Copy the output of this command, which on Kerrie's computer looked like this :
```

      # 1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
      Modeline "1440x900_75.00" 136.49 1440 1536 1688 1936 900 901 904 940

```

Paste this output into the "monitor" section of xorg.conf, restart the computer, and the new resolutions were available!

Good luck,
Callan

---

### Post by ravenwere on 2007-10-11
Upgraded the other PC to gutsy and the configuration is changed. It didn't pick up my video card but it picked up the monitor. Relevant sections of the xorg.conf as follows:

Section "Device"
    Identifier  "Nvidia 7600GT"
    Driver      "nvidia"
    BusID      "PCI:1:0:0"
    Option     "UseFBDev"   "true"
EndSection

Section "Monitor"
    Identifier  "Syncmaster"
    Option     "DPMS"
    Horizsync 30-81
    Vertrefresh  56-75
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device    "Nvidia 7600GT"
    Monitor   "Syncmaster"
    DefaultDepth 24
    SubSection "Display"
          Modes    "1440x900" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



If you end up with the terminal login because xwindows fails to load at any time use the sudo dpkg-reconfigure xserver-xorg command at the terminal to set up your xorg.conf file again from scratch.

---

### Post by 1Frothy on 2007-10-11
Thanks lots for everyones replies, specially ravenwere and overdrank :KS

I'm now running at 1680x1050 and very happy again!

---

### Post by corowakid on 2007-10-11
> **1Frothy said:**
> I installed restricted drivers for my TNT2 based video card. Now the resolution is no longer 1680x1050 but maximum of 800x600. I just can't find an option to change it. Please help,

FWIW, you might well look here:

[http://albertomilone.com](http://albertomilone.com)

He's put up great tutorials for nVidia drivers, and you can save/print those instructions you might find handy.  Worked 100% for me.

---

### Post by 1Frothy on 2007-10-11
Thanks for the link, just having a look now!

---

### Post by dcstar on 2007-10-12
> **ravenwere said:**
> 
.........
I would agree with Overdrank that given the age of this card you will prob. get more options with a defaultdepth of 16.
.........

Older video cards don't have newer widescreen resolutions built into them, so when the X server does a DDC probe if only receives the resolutions the card can provide - even though they are (usually) capable of displaying far more than what they were built for.

Remember that when a lot of these old cards were built, widescreens were rare so you can't really blame the manufacturers for not being able to guess the eventual resolutions that these things came out with.

Adding in the manual "modeline" entries (as shown by other posters) will solve this problem, as the X server now just doesn't rely on the outdated information that the card supplies.

The colour depth available will depend on the resolution used and the card RAM, so get the resolution right and then try for the maximum colour depth.

---

### Post by ravenwere on 2007-10-13
Hi David, Thanks for that clarification. This is not an area I would claim to know much about. I seem to remember installing the ati supplied linux driver at one stage and ending up with many modeline entries in xorg.conf but at the time not realizing how these entries were determined or how the information was applied.

Thanks Callan for the gtf info. I will play around with that a little more.

Good Luck 1Frothy

All the best,
R

---

