---
title: "Newbie needs help with Powerbook G4 500 Titanium"
date: 2010-06-04
forum: Apple Hardware Users
---

### Post by Semperfive on 2010-06-04
I just installed Ubuntu 9.04 ppc on my Powerbook G4 500 Titanium.

[This one]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_500.html")

I can only get it to run in Low Graphic mode.

I really don't know what I'm doing.  I've tried sudo gedit /etc/X11/xorg.conf with different settings I've found on the forum, but I can't find one that gives me better resolution.

I'd even be willing to try different versions of Ubuntu if anyone thinks it would help

Any Ideas?

---

### Post by linuxopjemac on 2010-06-05
You can stay in 9.04 if you like it.

Start with this file and if it does not work give me the output of

```
cvt 1152 768
cvt 896 600
cvt 720 480

```
and:
```
sudo cat /var/log/Xorg.0.log
```

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"false"
	Option		"SWcursor" 		"true"
	Option 		"ForcePCIMode" 		"true"
	Option 		"XAANoOffscreenPixmaps"
Option "NoInt10" "true"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
#	InputDevice	"Generic Keyboard"
#	InputDevice	"Configured Mouse"
#	InputDevice	"Synaptics Touchpad"
#	Option "AIGLX"	"true"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection
```


Please tell us if it works.

---

### Post by Semperfive on 2010-06-05
That totally worked, kinda.  At first It was really hard to see the screen because it was jumping and not centered after I updated the xorg.conf per your instructions.  I was able to get into the display settings and change it to 1024x768.  Now it looks good except about and inch and a half is black on the right of the screen.  I think I need the display settings to be 1152x768 but that setting is not there.  

You get the "Awesome Hat" for the day!!

Any ideas on how to get 1152x768?

---

### Post by linuxopjemac on 2010-06-05
Give me the output of this one:
```

cvt 1152 768
```

---

### Post by Semperfive on 2010-06-05
# 1152x768 59.78 Hz (CVT) hsync: 47.71 kHz; pclk: 71.75 MHz
Modeline "1152x768_60.00"   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync

Here you go

---

### Post by linuxopjemac on 2010-06-05
Try this:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"false"
	Option		"SWcursor" 		"true"
	Option 		"ForcePCIMode" 		"true"
	Option 		"XAANoOffscreenPixmaps"
Option "NoInt10" "true"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
# 1152x768 59.78 Hz (CVT) hsync: 47.71 kHz; pclk: 71.75 MHz
Modeline "1152x768_60.00" 71.75 1152 1216 1328 1504 768 771 781 798 -hsync +vsync
Option "PreferredMode" "1152x768_60.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x768" "896x600" "720x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by Semperfive on 2010-06-05
linuxopjemac,

Thank you very much!!!  That worked perfectly.

How do I get the Ctrl button to function as my right-click?  This Powerbook only has one button.

Also, when I close the lid, the screen stays on.

---

### Post by shawnhcorey on 2010-06-05
> **Semperfive said:**
> linuxopjemac,

Thank you very much!!!  That worked perfectly.

How do I get the Ctrl button to function as my right-click?  This Powerbook only has one button.

Also, when I close the lid, the screen stays on.

F12 is the right-click button; F11 is middle-click.  Holding down the 'fn' key while pressing F12 will eject the CD.

Have you tried suspending from the Quit button at the right-hand side of the top panel?

---

### Post by Semperfive on 2010-06-05
Thanks, that works

---

### Post by linuxopjemac on 2010-06-06
another happy user ;)

---

### Post by sha.goyjo on 2010-06-06
You should also see about using the appletouch module to allow you to use two finger scroll and click, as well as three finger click. Could you tell us the output of 
```

lsmod

```
please?

---

### Post by Semperfive on 2010-06-06
Module                  Size  Used by
binfmt_misc             9464  1 
ppdev                   8600  0 
lp                     10244  0 
parport                38132  2 ppdev,lp
uinput                  9072  2 
ipv6                  283668  10 
sbp2                   22668  0 
apm_emu                 1940  0 
apm_emulation           8208  2 apm_emu
snd_powermac           63588  2 
snd_pcm_oss            45156  0 
snd_mixer_oss          18880  1 snd_pcm_oss
snd_pcm                83224  2 snd_powermac,snd_pcm_oss
snd_seq_dummy           2848  0 
snd_seq_oss            34084  0 
snd_seq_midi            7436  0 
snd_rawmidi            25008  1 snd_seq_midi
snd_seq_midi_event      7184  2 snd_seq_oss,snd_seq_midi
snd_seq                57596  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24532  2 snd_pcm,snd_seq
snd_seq_device          7788  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3276  0 
snd                    67724  13 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              13748  1 iptable_filter
soundcore               7188  1 snd
pcmcia                 37908  0 
x_tables               17812  1 ip_tables
yenta_socket           27372  1 
snd_page_alloc          9748  1 snd_pcm
airport                 5040  0 
rsrc_nonstatic         10900  1 yenta_socket
pmac_zilog             18176  0 
orinoco                67756  1 airport
rtc_generic             1948  0 
pcmcia_core            40112  3 pcmcia,yenta_socket,rsrc_nonstatic
serial_core            23652  1 pmac_zilog
evdev                  11328  16 
windfarm_core          11064  0 
ohci1394               35320  0 
ieee1394               93164  2 sbp2,ohci1394
sungem                 32172  0 
sungem_phy             11656  1 sungem
uninorth_agp            9188  1 
agpgart                39572  1 uninorth_agp

Two finger scrolling would be cool

---

### Post by sha.goyjo on 2010-06-06
Try using 
```

$sudo modprobe appletouch

```
And tell me what the terminal outputs. If it says nothing, that is good. Then try 
```

$lsmod

```
again, and see if appletouch is in there. If it is,
```

$sudo gedit /etc/modules

```
and add the line
```

appletouch

```
to the end. Also, see if you can add (or create) this in your /etc/X11/xorg.conf

```

Section "ServerLayout"
        InputDevice    "Synaptics" "CorePointer"
        InputDevice    "Mouse0"    "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
       Identifier      "Synaptics"
       Driver          "synaptics"
       Option          "Device"                "/dev/input/mice"
       Option          "Protocol"              "auto-dev"
       Option          "LeftEdge"              "50"
       Option          "RightEdge"             "840"
       Option          "TopEdge"               "30"
       Option          "BottomEdge"            "320"
       Option          "MinSpeed"              "0.2"
       Option          "MaxSpeed"              "1.5"
       Option          "AccelFactor"           "0.1"
       Option          "SHMConfig"             "on"
       Option          "RTCornerButton"        "3"
       Option          "LTCornerButton"        "2"
       Option          "FingerLow"             "12"
       Option          "FingerHigh"            "20"
       Option          "MaxTapTime"            "120"  
       Option          "HorizScrollDelta"      "15"
       Option          "VertScrollDelta"       "15"
       Option          "VertEdgeScroll"        "off"
       Option          "HorizEdgeScroll"       "off"
       Option          "VertTwoFingerScroll"   "on"
       Option          "HorizTwoFingerScroll"  "on"
EndSection

```

That should work.

---

### Post by linuxopjemac on 2010-06-06
Nice try Sha.Goyjo, but I am afraid that that is a little bit too much for these old laptops. These laptops can't do what modern touchscreens can. It's a trackpad together with a mouse button pad. You can't even use gsynaptics.

---

### Post by sha.goyjo on 2010-06-06
linuxopjemac, two things. One, stop being snarky. None of us have the time for it at the rate bug reports are coming in. Two, although the appletouch module was orignally written for post 2005 aluminum powerbooks, there is the possibility that since his system uses a usb trackpad from the same manufacturer (and has the same capabilities listed by apple on their website) that it might work. If not, we'll have to fall back on johannes berg's appletrackpad module, which is more tricky. I wanted to try this out first, as it is easier.

---

### Post by Macalla on 2010-08-17
Hi everyone, I just registered and wanted to thank the people who posted in this forum as the information contained here was instrumental in aiding the set up of my 10 year old G4 Titanium Powerbook with accelerated hardware graphics rendering.

I, like the OP, had problems getting the autoconfiguration to recognize the display and was only able to boot into the CLI. After spending several hours editing the xorg.conf file, I managed the low-res mode with the "r128" driver. Then discovered 'fbdev' worked but with minimal hardware acceleration. A day later, after scouring the 'net extensively I got the 'r128' driver to work with additional "Modelines". Here is my final xorg.config file, hope it helps someone. I didn't specify nor address the other hardware as I had no issues.

Glxgears went from 500 (with fbdev driver) to 2000+ (with r128 driver). GLMatrix screensaver works!

Hardware details:
Powerbook Titanium G4 500MHz (circa 2001)
RAM 1GB PC100
Graphics Rage 128 AGP 2x 8MB VRAM
Resolution 1152x768

====================
```

Section     "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "pex5"
    Load    "record"
    Load    "type1"
    Load    "vbe"
    Load    "xie"
EndSection


Section        "Device"
    Identifier    "ATI Rage 128 M3"
    Option        "UseFBDev"
    Driver        "r128"
    VideoRam    8192
EndSection


Section        "Monitor"
    Identifier    "Apple PowerBook G4"
    HorizSync    30-100
    VertRefresh    50-160
    Option        "DPMS"
    Modeline    "1152x768" 64.994 1152 1178 1314 1472 768 771 777 806 +HSync -VSync
EndSection


Section        "Screen"
    Identifier    "Default Screen"
    Device        "ATI Rage 128 M3"
    Monitor        "Apple PowerBook G4"
    DefaultDepth    16

    SubSection    "Display"
    Depth        8
    Modes        "1152x768"
    EndSubSection

    SubSection    "Display"
    Depth        16
    Modes        "1152x768"
    EndSubSection
EndSection


Section        "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection


Section        "DRI"
    Mode    0666
EndSection

```

---

### Post by linuxopjemac on 2010-08-17
Great, it found its way on my website (last PowerBook entry)

[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)

---

### Post by Macalla on 2010-08-17
Excellent! Incidentally, your site was one of my sources for information as well.

---

### Post by linuxopjemac on 2010-08-17
Not so incidentally, it's THE source of xorg.conf files on powerpc. You will not find more xorg.conf files on one site.

---

### Post by Macalla on 2010-08-17
I am also a new fan of your site :p.
Got myself registered and hopefully will have a report on another Ubuntu install in an old B&W G3 (G4 upgraded) with a Mac-ROM-flashed PCI Nvidia FX5200 card.

---

### Post by linuxopjemac on 2010-08-17
You are welcome to post anything you find useful.

---

### Post by ikmac on 2010-10-19
Hi !

I'm french, and my english is so bad !!!

My config is PowerBook Titanium 400 - ATI Rage Pro 8Mo

I'v tried to install 10.10 Maverick Ubuntu distrib....

No problem to install but at reboot i've video artefact after the screen who only said "Ubuntu 10.10"

I've tried Alt-F1 to log in the text console :

User name OK password OK

and "sudo edit /etc/X11/xorg.conf" is empty 

Help me please

iK

---

### Post by linuxopjemac on 2010-10-19
which one? link in everymac.com please

---

### Post by ikmac on 2010-10-19
this one, the the original PowerBook G4

[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_400.html]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_400.html")

Thanks for your help !!!

---

### Post by linuxopjemac on 2010-10-20
in a terminal:
```
wget http://mac.linux.be/files/xorg/powerbook7.txt
sudo mv powerbook7.txt /etc/X11/xorg.conf
```

if that does not work, try:
```
wget http://mac.linux.be/files/xorg/powerbook9.txt
sudo mv powerbook9.txt /etc/X11/xorg.conf
```

Let me know which one works for you.

---

### Post by ikmac on 2010-10-20
Ok thanks but i've no network connection

i'm going to type text in local in the xorg.conf

Thks

I say you later if it works

---

### Post by tyce on 2011-02-07
Since i was young, the Ti PowerBook was always a fantasy of mine to own. I've since owned several MacBook pros, iMacs, minis, etc but I've found a good deal on a slightly used Ti and I'm thinking of pulling the trigger. 

My question to you guys; how is the performance under ubuntu? This model is the 550 and I'll more/less just be using it to code on via iterm. Should I take this chance at nostalgia, or would the hundred or so dollars be better spent elsewhere?

Thanks in advance,

---

