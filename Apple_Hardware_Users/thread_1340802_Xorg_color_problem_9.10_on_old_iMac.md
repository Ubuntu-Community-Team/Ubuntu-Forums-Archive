---
title: "Xorg color problem: 9.10 on old iMac"
date: 2009-11-29
forum: Apple Hardware Users
---

### Post by julianb on 2009-11-29
I have an old iMac with an install of Ubuntu 9.10 (minimal) and IceWM. It has only 64MB RAM.

The screen resolution is pretty high, 11xx by 7xx (eleven hundred something by seven hundred something), if I remember right.

Colors are messed up. I'm no expert but it looks like it is running in 256 color mode because if you look at something like the brown gradients used for the background of this forum, there are only a few colors of brown displayed and they don't "fade" smoothly into each other. Photographs look terrible in this number of colors.

I tried to figure out how to use xrandr, and xorg.conf, but I didn't actually have an xorg.conf file. Tried sudo dpkg-reconfigure Xorg 
It doesn't seem to do anything.

I've been searching the internet a lot to see about how to work on Xorg, and I'm not sure how much   has changed with the coming of the newest Ubuntu. 

I'd really like to get the colors on this thing fixed because the person who will be using the machine is planning to use it to do visual layout on wordpress sites.

---

### Post by linuxopjemac on 2009-11-29
what's the exact model ?

---

### Post by julianb on 2009-11-29
On the bottom it says it's an iMac GX; the model is : M5521



it's a gray color, if that helps

it also says that i was wrong about 64mb RAM - the label says 128MB and i'm pretty sure nobody downgraded it.

---

### Post by linuxopjemac on 2009-11-29
Ok, I found that's the iMac G3 from summer 2000....I will look for a Xorg.conf file

Monitor: 15"

GPU: ATI RAGE 128 Pro

VRAM: 8 MB SGRAM

Max Resolution: 24 bit 1024x768

---

### Post by linuxopjemac on 2009-11-29
```
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/cyrillic"
FontPath "/usr/share/X11/100dpi/:unscaled"
FontPath "/usr/share/X11/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi" # paths to defoma fonts
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType"
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID"

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 60-60
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection
```

---

### Post by julianb on 2009-11-30
Thanks for trying to help. I haven't had success yet. I do not already have the driver ("ati") mentioned in that xorg.conf file. 

In response to a google search about installing ati drivers, i saw instructions that said to do

sudo apt-get install linux-restricted-modules $(uname -r)

and 

sudo apt-get install xorg-driver-fglrx

and

depmod -a

====
i broke my xorg.conf file by trying stuff out and will try more later. off to bed, for now.

PS - If you know how to reinstall your OS, then don't be afraid of breaking it. Every time you mess things up, it's an opportunity to learn.

---

### Post by linuxopjemac on 2009-11-30
I don't think you need to install that driver, it should work out of the box to my opinion

---

### Post by julianb on 2009-12-01
I suppose I should have mentioned earlier, it gave me an error message saying I did not have the driver "ati".

I tried removing the line where it says

driver "ati"

and that made the xorg.conf file broken. 

now I have to go in using the install CD to remove the xorg.conf file because the machine otherwise boots up, then launches xdm and xorg automatically which results in a black screen.

---

### Post by linuxopjemac on 2009-12-01
you can also start with framebuffer, so without any fancy acceleration...

```
Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:18:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
EndSection

Section "Module"
Disable "glx"
Disable "dri"
EndSection
```

---

### Post by linuxopjemac on 2009-12-01
have a look at this great thread:
[http://forums.debian.net/viewtopic.php?f=16&t=20481](http://forums.debian.net/viewtopic.php?f=16&t=20481)

---

### Post by oswaldkelso on 2009-12-01
[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

If it's gray then it's probably a se model

[http://oswaldkelso.blogspot.com/2009/11/imac-xorgconf-ppc-all-versions.html](http://oswaldkelso.blogspot.com/2009/11/imac-xorgconf-ppc-all-versions.html)

```
lspci
``` will list your graphics card and let you choose the correct xorg.conf file

I've never heard of any non-free ati drivers for the PPC imac

---

### Post by linuxopjemac on 2009-12-01
if you like to tweak the monitor settings, you can do the following:

In a terminal, generate xorg.conf modeline by executing
```
gtf <width> <height> <refresh>
```
Note. For LCD displays, used in notebooks, the refresh should be no more than 60.

The output string may look for example as follows:

```
Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
```

"1440x900_60.00" is the mode name; 1440 is width, 900 is height, and 60 is refresh of the new mode that were given to the gtf.

Open xorg.conf and paste the output of gtf to the Monitor section. The Monitor section looks as below:

```
Section "Monitor"
	Identifier "monitor1"
	VendorName "Generic"
	ModelName "1024x768 @ 70 Hz"
	HorizSync 31.5-57.0
	VertRefresh 50-70
	# TV fullscreen mode or DVD fullscreen output.
	# 768x576 @ 79 Hz, 50 kHz hsync
	ModeLine "768x576" 50.00 768 832 846 1000 576 590 595 630
	# 768x576 @ 100 Hz, 61.6 kHz hsync
	ModeLine "768x576" 63.07 768 800 960 1024 576 578 590 616
	Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection

```

The last line is the line that tells Xorg to use that resolution and refresh. You have to specify that as default in the Subsection "Display" of your choosing under Section "Screen" as the following:

```
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   "1440x900_60.00"
        EndSubSection
EndSection
```
-----------------------------------------------

BTW, you will have different output, as your screen cannot handle such a huge resolution.

---

### Post by julianb on 2009-12-02
This is what worked for me. I am still not sure what is the deal with the ATI driver stuff - i just commented out the whole section to see what would happen and now my colors work. I did not actually try to install ati drivers yet. 

```

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/cyrillic"
FontPath "/usr/share/X11/100dpi/:unscaled"
FontPath "/usr/share/X11/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi" # paths to defoma fonts
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType"
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

# Section "Device"
# Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
# Driver "ati"
# Option "UseFBDev" "true"
# EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
HorizSync 60-60
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768_60.00"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

```

---

### Post by linuxopjemac on 2009-12-03
I am glad to hear that it worked for you.

---

