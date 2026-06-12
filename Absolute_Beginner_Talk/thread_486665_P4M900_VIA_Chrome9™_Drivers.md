---
title: "P4M900 VIA Chrome9™ Drivers"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by fifafrazer on 2007-06-28
I want to install Xubuntu on my laptop:

Fujitsu Siemens Notebook AMILO Pro Edit V3515 15.4

First of all I wasn't able to install the OS, because the only resolution available on the live cd was 640*480, and then the install windows are so big, that you can't click on the "OK" buttons, because they are underneath the lower edge of the screen. It should be able to install the OS by downloading the alternate disc, but then I figured out that Xubuntu dont support the integrated graphics card, which is:

P4M900 VIA Chrome9™ HC integrated graphics (VN896)

I've read some old posts on the internet saying, that there are no proper linux drivers for this chipset. The openchrome drivers only support 2D and video playback. Are there any news regarding this chipset? I would simply love to get Xubuntu on my laptop :)

---

### Post by overdrank on 2007-06-28
> **fifafrazer said:**
> I want to install Xubuntu on my laptop:

Fujitsu Siemens Notebook AMILO Pro Edit V3515 15.4

First of all I wasn't able to install the OS, because the only resolution available on the live cd was 640*480, and then the install windows are so big, that you can't click on the "OK" buttons, because they are underneath the lower edge of the screen. It should be able to install the OS by downloading the alternate disc, but then I figured out that Xubuntu dont support the integrated graphics card, which is:

P4M900 VIA Chrome9™ HC integrated graphics (VN896)

I've read some old posts on the internet saying, that there are no proper linux drivers for this chipset. The openchrome drivers only support 2D and video playback. Are there any news regarding this chipset? I would simply love to get Xubuntu on my laptop :)

HI I have found this link
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=101](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=101)
Some are for edgy and feisty and some are for just edgy. The bad part is that it says you have to build. I have never tried that but if it is something you want to try. Good luck!

---

### Post by fifafrazer on 2007-06-28
And they only support 2D and video playback, but no 3d?

---

### Post by santoxyz on 2007-07-13
no 3d and buggy video Xv (pc freezes when you close player) ...

good, no?

they say rev79 of driver will have official and complete support for vn896 ... but when will it be released?

anyway, i use it : videos works fine with X11/shm and vertical scrolling is good (everything is better than VESA driver !)

if you use original generic-15 kernel you can download from viaarena the precompiled driver; otherwise you have to compile the sources (there are detailed instructions at viaarena )

---

### Post by virtual_reality on 2007-10-27
> **overdrank said:**
> HI I have found this link
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=101](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=101)
Some are for edgy and feisty and some are for just edgy. The bad part is that it says you have to build. I have never tried that but if it is something you want to try. Good luck!

how can I build it? please help :( would it worsk for 7.10?

---

### Post by santoxyz on 2007-11-26
there are detailed instructions enclosed with the sources.
When you compiled your driver you only have to install only via_drv.so :
cp -f via_drv.so /usr/lib/xorg/modules/drivers/via_drv.so  







this is my /etc/X11/xorg.conf  :

-------------------------





Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "bitmap"
Load "extmod"
Load "freetype"
Load "int10"
Load "vbe"

Load "dri"
Load "glx"
# Load "ddc"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "it"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "VN896"
Driver "via"
BusID "PCI:1:0:0"
Option "ActiveDevice" "LCD,CRT"
Option "NoDDCValue" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "VN896"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800" "640x480"
# Virtual 1280 800
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection



-------------------


good luck !

---

### Post by santoxyz on 2007-12-31
i switched to openchrome drivers and i suggest them! 
download last svn sources and compile it....

for the installation, i workarounded moving the bars from up and down to left and right!

---

### Post by fifafrazer on 2008-01-06
Why do you prefer OpenChrome over Vesa... Do they have increased performance, because vesa is software driven?

---

