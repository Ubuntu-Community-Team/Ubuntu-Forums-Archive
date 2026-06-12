---
title: "Gutsy low resolution problem nvidia"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-21
Gutsy has screwed my goose.  I tried first an ungrade, and then a fresh install into another partition and both instances I get a low resolution display.  When Ubuntu boots, I get presented a low resolution warning window that wants me to select my graphics card and monitor - but there is no way to commit the changes I've made.  To continue, all I can do is press Cancel.  

When I finally get into Ubuntu, I'm stuck with 800x600 resolution.  I'm running an nVidia 6200 card that worked just fine with Feisty - including Beryl.

Any help to get me back is immensely appreciated.

Thanks

Carl

---

### Post by Qwerty_ on 2007-10-21
You need to install the restricted drivers.

System>Administration>Restricted Drivers Manager.

---

### Post by mikeyphi on 2007-10-21
And * first * confirm that the Software sources are enabled!

---

### Post by magli on 2007-10-21
I have an nvidia geforce FX Go5650 on a dell d800. I have had a resolution problem every time I have installed or upgraded ubuntu.

Have you enabled the restricted nvidia modules? -You will need this to get the graphics effects which you had with beryl.

To fix the resolution problem, you may have to edit your xorg.conf file. 

First make a backup of your current one:
```
$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-orig
```

Then xorg.conf with whatever editor you want, as root. I suggest you use gedit, like this:
```
$gksudo gedit /etc/X11/xorg.conf
```

Scroll down this file until you get to the "screen" section, and find the following lines:
```

Monitor        "Generic Monitor"
DefaultDepth   24

```

After these lines, you should have a subsection called "Display" (you may even have several). Make sure that the correct resolution of your screen is entered here. For reference, here is what my "Screen" section looks like:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV31M [GeForce FX Go5650]"
    Monitor        "Generic Monitor"
    DefaultDepth   24
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection

```

You then need to restart X - either by logging out, or by hitting "CTRL+ALT+BACKSPACE"

If you still have problems, post the output of the 'lsmod' command, aswell as the contents of your xorg.conf.

Cheers.

---

### Post by cwmoser on 2007-10-21
I fixed this problem by editing /etc/X11/xorg.conf  - at Section"Device", Driver "nvidia", I changed "nvidia" to "nv".

That got me back in and I got my resolution back to 1680x1050 and in "Twin View"

Now, I'm back where I stated at -- that is trying to get the visual effects to work.

When I go to System -> Preferences -> Appearance, press the Visual Effects tab, and then select either of Normal/Extra/Custom, my screen goes completely white for about 45 seconds and then it comes back.  But the Visual Effects setting stay at None.

I've got these installed:


linux-restricted-modules-2.6.22.14-386
linux-restricted-modules-2.6.22.14-generic
nvidia-glx-new
nvidia-kernel-common
restricted-manager
restricted-manager-core
smartdimmer
xserver-xorg-video-nv

Any ideas why I cannot get the Visual Effects to work?

Carl

---

### Post by magli on 2007-10-21
"nvidia" is the name of the restricted, propietry driver from nvidia.
"nv" is the name of an alternative open source driver (which, does not support the compiz effects)
When you changed the Driver line in you xorg.conf, you essentially stopped using the restricted driver, which you need in order to get the effects to work.

---

### Post by cwmoser on 2007-10-21
After enabling the restricted drivers via System -> Administration -> Restricted Drivers, I was able to get my resolution back to 1680x1050 and dual monitor desktop.

I checked by /etc/X11/xorg.conf file and it changed from "nv" to "nvidia".  BUT, if I try to enable the visual effects, I get this white screen for 45 seconds and no visual effects.

I also tried removing compiz and reinstalling -- but that did not help.

Carl

---

### Post by euthyfro on 2007-10-21
> **magli said:**
> I have an nvidia geforce FX Go5650 on a dell d800. I have had a resolution problem every time I have installed or upgraded ubuntu.

Have you enabled the restricted nvidia modules? -You will need this to get the graphics effects which you had with beryl.

To fix the resolution problem, you may have to edit your xorg.conf file. 

First make a backup of your current one:
```
$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-orig
```

Then xorg.conf with whatever editor you want, as root. I suggest you use gedit, like this:
```
$gksudo gedit /etc/X11/xorg.conf
```

Scroll down this file until you get to the "screen" section, and find the following lines:
```

Monitor        "Generic Monitor"
DefaultDepth   24

```

After these lines, you should have a subsection called "Display" (you may even have several). Make sure that the correct resolution of your screen is entered here. For reference, here is what my "Screen" section looks like:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV31M [GeForce FX Go5650]"
    Monitor        "Generic Monitor"
    DefaultDepth   24
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection

```

You then need to restart X - either by logging out, or by hitting "CTRL+ALT+BACKSPACE"

If you still have problems, post the output of the 'lsmod' command, aswell as the contents of your xorg.conf.

Cheers.

yes, that's what i tried to do but my xorg.conf is: 

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:5:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

my "lsmod" read out is:

Module                  Size  Used by
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
ac                      6148  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  24 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
agpgart                35016  1 nvidia
psmouse                39952  0 
k8temp                  6656  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
serio_raw               8068  0 
i2c_nforce2             7040  0 
pcspkr                  4224  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  2 nvidia,i2c_nforce2
ipv6                  273892  12 
evdev                  11136  3 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
sata_nv                20612  3 
floppy                 60004  0 
ohci_hcd               22916  0 
ehci_hcd               36492  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
forcedeth              51592  0 
usbcore               138632  3 ohci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

should i just edit the default screen section? & if so, what should i put in the device section since i've got a 7300LE

---

### Post by magli on 2007-10-21
I am not sure. I guess you can try editing the reslution in the default screen... but I don't know.

You can also try running "nvidia-settings" - it may allow you to adjust the resolution.

---

### Post by JohnSGruber on 2007-10-21
> **euthyfro said:**
> yes, that's what i tried to do but my xorg.conf is: 

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

...


I assume that you too are having resolution problems.

The configuration file you posted has only 1 mode and that's 640x480. As or more importantly it lists a virtual screen size of 640x480 too.

It might make sense to use Displays and Graphics to set up your monitor. After you
do that you may have to add back the following two lines to where they are now:

 Option "AddARGBGLXVisuals" "True"
 Option "NoLogo" "True"

If you feel confident in editing the file you could do that directly. If not, there is a command to try, but the first thing to do is to get the resolution correct.

Was your resolution correct with the old driver? Have you used Displays and Graphics under the Administration menu? You might be able to go back to the non-proprietary driver, use Displays and Graphics there to select your monitor, verify your resolution, then enable the proprietary driver. By doing things in that order you shouldn't have to hand edit the xorg.conf file.

---

### Post by ilushkin on 2007-11-04
I have the similar problem after upgrade. I have Nvidia and Samsung SyncMaster 906bw
How should I edit xorg.conf?

here is my Xorg.Conf

---------------------------------------
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 905DF(X)/955DF(X)/CD195A"
	Horizsync	30-85
	Vertrefresh	50-160
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1152x768@54"	"1280x854"	"800x600@60"	"1280x768@60"	"800x600@85"	"1280x720@60"	"800x600@75"	"1280x800@75"	"800x600@72"	"1280x768@75"	"800x600@56"	"1280x720@50"	"720x400@85"	"1280x800@60"	"640x350@85"	"1440x900@75"	"640x400@85"	"1440x900@60"	"1600x1024@60"	"1680x1050@60"	"1680x1050@75"	"1920x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #         
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #         
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #         
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by overdrank on 2007-11-04
> **ilushkin said:**
> I have the similar problem after upgrade. I have Nvidia and Samsung SyncMaster 906bw
How should I edit xorg.conf?

here is my Xorg.Conf

```
---------------------------------------
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 905DF(X)/955DF(X)/CD195A"
	Horizsync	30-85
	Vertrefresh	50-160
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1152x768@54"	"1280x854"	"800x600@60"	"1280x768@60"	"800x600@85"	"1280x720@60"	"800x600@75"	"1280x800@75"	"800x600@72"	"1280x768@75"	"800x600@56"	"1280x720@50"	"720x400@85"	"1280x800@60"	"640x350@85"	"1440x900@75"	"640x400@85"	"1440x900@60"	"1600x1024@60"	"1680x1050@60"	"1680x1050@75"	"1920x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #         
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #         
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #         
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

Have you tried using the nvidia settings to change your resolution?

---

### Post by black drongo on 2007-11-05
hi 
i have similar problems with gutsy
when i use open source driver the resolution is ok (my default is 1440X900 on a viewsonic 1930 wm monitor)
but the moment i enable the restricted driver( nvidia-glx), and restarts, the res goes to 640X 480. and i cant get it to work with 1440X900. i tried to install nvidia-glx-new from synaptic, but even after installation,restricted driver manager says "restricted driver not in use".and when i enable it, it replaces nvidia-glx-new with nvidia-glx. to give only low res on restart.
in effect i am not able to use compiz.
plz help, my knowledge in linux is next to nothing, so detailed suggestions will be appreciated. thank you..
 in addition when i tried to install nvidia -settings,it installs ,but on running, a window which has nothing much on it appears giving no option to change res

---

### Post by JohnSGruber on 2007-11-06
@ilushkin
Your xorg.conf file seems to set you for some pretty high resolutions, but you don't say what resolution you are aiming for.

Your file does seem to be somewhat messed up. I don't think you are using either of the monitor1 entries, and probably shouldn't have two sections of the same name in any case. I don't know what Xorg will do with your configuration file, but I would hope it would use the one and only serverlayout section and then use the reasonable screen, device, and monitor sections at the top of the file.

Maybe it would be best to save your current /etc/X11/xorg.conf file somewhere and start it over from the original configuration with:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You enter this command into a terminal window which you open with the menu choice Applications->Accessories->Terminal

That will disable the nvidia driver for the time being, but your resolution might look good. Then use System->Administration->Screens and Graphics to set the resolution permanently. I don't think there is an entry for your 906bw but it looks to me like the Samsung SyncMaster 910MP has about the same parameters.

Then use System_Administration->Restricted Drivers to turn on the nvidia proprietary driver you need.

After that you can try the different resolutions available by holding Control and Alt while pressing the + and the - key on the **numeric keypad**

If that doesnt give you the resolution you want please tell us the resolution you are looking for (I assume it might be 1280x900 at 60Hz since that what the 906bw manual seems to recommend), and attach both the /etc/X11/xorg.conf file and the /var/log/Xorg.0.log file from when you try. That last file will tell us what resolutions were eliminated by the driver and why.

---

### Post by JohnSGruber on 2007-11-06
@Black Drongo:
I don't think the version of nvidia driver selected by the restricted driver program is causing the resolution problem. I have an older card than you and am using the old nvidia-legacy driver and I was finally able to get 1280x1024 resolution on my viewsonic monitor.

I'd suggest that you might try the following:

Disable the restricted driver with System->Administration->Restricted Driver Manager

Use System->Administration->Screens and Graphics to select the generic LCD 1440x900 resolution monitor and then select this same resolution (if your system is set up like mine under gutsy you don't have a monitor entry for the viewsonic 1930wm). I believe this is a wide screen monitor so you should check the wide screen checkbox when selecting the generic LCD 1440x900 monitor because I think this is considered a wide-screen resolution.

Check to see that the screen still looks fine. It probably won't change at all but the underlying file will be changed to allow this resolution and that's the point of doing this now.

Then enable the restricted driver System->Administration->Restricted Drivers Manager and see what you have.

You should be able to see all of the possible resolutions at that point by holding Control and Alternate and then pressing and releasing the + and - keys on the **Numeric Keypad**. The + and - keys on the regular part of the keyboard don't work.

If that doesn't give the 1440x900 resolution please tell us what happened and attach both /etc/X11/xorg.conf and the /var/log/Xorg.0.log from when you tried it. If you wind up having the system use a failsafe mode the Xorg.0.log file can be from using the failsafe mode and it would then be good to see /var/log/Xorg.0.log.old

Good luck and please tell us how you did.

---

### Post by black drongo on 2007-11-07
thank u john 
first of all i dont have a graphics "card". but i do have an onboard graphics chip which is NVIDIA geforce 6150.
now i tried as u suggested, the resolution is holding as long as i dont reboot. on rebooting it asks low resolution, do you want to configure? i chose not to. after logging in, its back to 800X600. and screen( screens&graphics) says plug & play monitor with only 2 options 800x600 640x480. restricted driver is enabled. strangely xorg shows the resolution 1440x900.though thats not available. previous to this test, with opensource driver 4 nvidia and viewsonic 191 b setting i was getting the res. but compiz fusion will not work

---

### Post by JohnSGruber on 2007-11-07
@black drongo

Sounds like the xorg server program tried the changed configuration but had an error and then went into "fail safe" mode at low resolution. The question is what is the error.

If you haven't restarted since the events you described, could you post Xorg.0.log.old ? As is often the case in this situation the Xorg.0.log file doesn't contain the errors that are causing the problem because it is from the successful logon at low resolution. The .old file may be from when the error was produced. If it is also from a "fail safe" logon we will have to do something else to see what the error is.

I assume you are rebooting as told to by the restricted driver manager. That's what activates the new driver. I don't know why the new driver would refuse to run on a configuration that's valid for the open source driver but maybe we can figure it out.

Are you using gutsy? Have you installed the proprietary nvidia driver using any method other than using the Restricted Driver Manager? (I'm wondering if the nvidia driver xorg uses matches the nvidia kernel driver, but I'm no doubt getting ahead of myself). Were your previous problems with reduced resolution while trying to use the proprietary driver after getting the same message or did it go directly into low resolution?

---

### Post by pappfer on 2007-11-07
First of all: I'm using Gutsy, and I have ATI Radeon 9600 graphics card.
I have exactly the same problem as **black drongo**. I also reinstalled Ubuntu about that cause I didn't know what was the cause of this problem. But after the new Ubuntu install it happened again, after enabling the restricted drivers.
Everytime I enable the restricted drivers and restart my PC I get this resolution problem.

There's one important thing to add: I always used restricted drivers. Compiz Fusion **never worked** for me **without** installing xserver-xgl and without enabling the restricted drivers. So i always installed these. And some days ago, from one day to another, the resolution problem appeared. I haven't touched restricted drivers at all, haven't installed anything. So I'm totally confused about how the problem came.

Another weird thing is that I uninstalled xserver-xgl and disabled restricted drivers and Compiz Fusion **works** now! As I already mentioned it never worked without xgl and restricted drivers before. Confusing, isn't it? :)

---

### Post by black drongo on 2007-11-09
john 
the problem gets worse, i realised now that my gutsy ( i upgraded from fiesty to gutsy) is not  automatically mounting flash drives, gives an error" incorrect filesystem" .though i can mount it from cli, it does not show in computer. further mouse pointer sometimes disappears, though i can make out when the cursor(or the void of it) moves over some icon. right now its such a state. being a tyro, no option of cli. i think i am going to try a clean install. not much data anyway.i am attaching all the xorg.0.log files i could find .the res prob happened two more times. dont know why, bcos it was stable before( the combination of viewsonic 191b screen and open source driver.). i will keep u posted on what happens. thanks for the help.

---

### Post by xzero1 on 2007-11-09
I had possibly a similar problem when I upgraded my kernel in gusty. Examining the xorg log, xorg was selecting the wrong resolution or timings for my monitor. Xorg setup defaults for generic lcd 1680x1050 did not work. Using settings from an old xorg config (feisty) got everything working ,including compiz.

---

### Post by JohnSGruber on 2007-11-09
@black drango
Given all of the problems you're having it seems reasonable to me to reinstall. I can't explain why the system would work some of the time and bomb out at other times with nothing changed.

I looked through the logs and don't see anything I recognize as a problem. There are errors in the xorg.0.log and xorg.0.log.old files saying you can't run features needed for compiz, but then that's because you are using the nv driver. I didn't notice the use of the proprietary nvidia driver, which makes sense since you are still trying to get the nv driver to run reliably.

Maybe someone else who knows more than I do will contribute something.

Otherwise, good luck with the reinstall. Please write back and let us all know how you did.

---

### Post by seanreynoldscs on 2008-01-29
I have Nvidia 6600 with 512.

When Install the ubuntu Nvidia new restricted drivers, i have no luck.

When i go to Nvidia and get their updated driver, i get one screen working. 
When I use the Screen And Resolution in ubuntu, i get the Low Resolution error. 
I had alot of trouble getting Compiz and Dual Screens. This is what i did.


Process:
Get new ubuntu 7.10 with updates: DONT INSTALL RESTRICTED DRIVER. 
Go to Nvidia and get their driver and install it.
Install Nvidia Settings through Synaptic Manager. (STAY AWAY FROM [Screen and Resolutions] It breaks the xorg.conf file)
Go to the Nvidia Settings and set Seperate X Screens with xinerama. Reboot (make sure to save the xorg.conf file each time) ( I had to cut and paste it because the Nvidia settings did not elevate when trying to save the xorg.conf file)
Go back to Nvidia Settings and set TwinView and merge the settings.(make sure to save the xorg.conf file each time)

and its all better.

To make it work, i had to get: ```
sudo apt-get install nvidia-settings
```
which uninstalled the restricted nvidia new drivers (if you had them installed).

Using Nvidia settings I was able to get both monitors with good resolution and Compiz using seperate x screens or Using TwinView. BUT I did not want either of those settings. Seperate X Screens wouldnt let me drag a window from one screen to another, and twin view gave me one big cube and when i maximized a window it went to both monitors full screen!

So i found out that if you go to Seperate X Screens and tick xinerama and restart, it sets that flag in your xorg.conf file but disables 3D! Then if you switch settings to Twinview once xinerama was already ticked, you get the 3d with the ability to drag windows from one screen to another, Two separate cubes, and Maximize to one screen only. Exactly what i wanted. 

Im sure there is a better way to do this, Im quite new to linux: but i got it to work, and that was how.

---

