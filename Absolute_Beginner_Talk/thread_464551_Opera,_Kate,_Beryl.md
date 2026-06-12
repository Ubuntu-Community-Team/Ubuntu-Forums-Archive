---
title: "Opera, Kate, Beryl"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-04
Hello,
I have the following problems:

1) I installed opera using the Adept package manager. The installation went on without any trouble. But when I try to open the browser it just hangs and terminates. It doesnt open at all. Right now I have removed it from my system. Is there an effective way of installing opera?

2) Kate works. But whenever I open a file using kate I get the following error messages:

[1] 5772
sudarshan@Lucky-Linux:~$ X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I noticed that whenever Adept is installing something, this same messages pop up. I dont know what they signify.

3) Finally, I am a bit of a sucker for eye candy so I installed Beryl using adept. I opened the beryl options menu and went through it. Seems nice. But how exactly do I start it? I mean do I need to enable the use of beryl somewhere?

4) I have also installed Wine. But I dont know how to use it.
Thankyou,
SS

---

### Post by overdrank on 2007-06-04
> **linuxnovice said:**
> Hello,
I have the following problems:

1) I installed opera using the Adept package manager. The installation went on without any trouble. But when I try to open the browser it just hangs and terminates. It doesnt open at all. Right now I have removed it from my system. Is there an effective way of installing opera?

2) Kate works. But whenever I open a file using kate I get the following error messages:

[1] 5772
sudarshan@Lucky-Linux:~$ X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I noticed that whenever Adept is installing something, this same messages pop up. I dont know what they signify.

3) Finally, I am a bit of a sucker for eye candy so I installed Beryl using adept. I opened the beryl options menu and went through it. Seems nice. But how exactly do I start it? I mean do I need to enable the use of beryl somewhere?

4) I have also installed Wine. But I dont know how to use it.
Thankyou,
SS

Hi and 1. opera dose not run in KDE
and three if you have installed beryl 
first which video card are you using ( ati for nvidia ) graphics card. then we can help:popcorn:

---

### Post by coolbrook on 2007-06-04
Did you try loading Opera to a blank page?  Coincidentally I installed it for the first time on Feisty and I noticed that there doesn't appear to be a plug-in for Adobe Flash Player.. either that or I'm completely daft with my attempts to install.  I have to re-install Opera since it can't see any plug-ins at all any more.

> opera dose not run in KDE

Good eye. I didn't notice his signature.

---

### Post by overdrank on 2007-06-04
> **coolbrook said:**
> Did you try loading Opera to a blank page?  Coincidentally I installed it for the first time on Feisty and I noticed that there doesn't appear to be a plug-in for Adobe Flash Player.. either that or I'm completely daft with my attempts to install.  I have to re-install Opera since it can't see any plug-ins at all any more.



Good eye. I didn't notice his signature.

TY TY And I bow :p

---

### Post by linuxnovice on 2007-06-04
I am afraid I dont have either nvidia or ati video card :(. I just have the ones that came with this laptop. But I tried Mandirva Live before installing Kubuntu and compiz worked in it really well. 

So there is no way installing opera on Kubuntu? Does opera work on Xubuntu? I would like to give Xubuntu a try sometime in the near future so maybe there I could make it work?

How about the problem I am having with Kate?

---

### Post by overdrank on 2007-06-04
> **linuxnovice said:**
> I am afraid I dont have either nvidia or ati video card :(. I just have the ones that came with this laptop. But I tried Mandirva Live before installing Kubuntu and compiz worked in it really well. 

So there is no way installing opera on Kubuntu? Does opera work on Xubuntu? I would like to give Xubuntu a try sometime in the near future so maybe there I could make it work?

How about the problem I am having with Kate?

Hi you said you have neither card? Can you post the command **_lspci_** in the terminal/ thanks I dont know about kate but I will search!;)

---

### Post by linuxnovice on 2007-06-04
Here is the details of lpsi:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

Thanks.

---

### Post by overdrank on 2007-06-04
> **linuxnovice said:**
> Here is the details of lpsi:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
[COLOR="Red"]00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)[/COLOR]
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

Thanks.

Hi you are right I have highlighted the graphics driver.
can you post the output of the command _*gksudo gedit /etc/X11/xorg.conf *_ to insure you have the proper drive in use.

---

### Post by linuxnovice on 2007-06-04
Here is the output of *kdesu kate /etc/X11/xorg.conf* :D

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
  identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1280 1024
    modes "1280x960@60" "1280x1024@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 1
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by overdrank on 2007-06-04
> **linuxnovice said:**
> Here is the output of *kdesu kate /etc/X11/xorg.conf* :D

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

[COLOR="Red"]Section "Device"
  identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  boardname "i810"[/COLOR]
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1280 1024
    modes "1280x960@60" "1280x1024@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 1
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection

Ok as you can see you are using the i810 driver so you can try this command
***sudo apt-get install xserver-xorg-video-intel***
But I do not use feisty and I found this in the threads on here. SO with that said please back up your xorg and then proceed if you like or do some more searches for you graphics drive on the forums. Good Luck and sorry I could not be of some more help:(

---

### Post by luciferin on 2007-06-04
First, try this from the terminal: ```
beryl-manager
```
If you don't like the icon you could just run the command beryl.  If it doesn't work post the error you get here.

Maybe I'm just crazy, but from the sound of things you've only opened up the settings manager (beryl-settings).


On a further note, Feisty should be able to grab any drivers your card needs to run from the Restricted Drivers Manager in the Administration menu.  In my opinion it tends to simplify things quite a bit.

---

### Post by zvacet on 2007-06-05
Download Opera from this page

[http://www.opera.com/download/]("http://www.opera.com/download/")


[http://www.opera.com/linux/docs/plugins/]("http://www.opera.com/linux/docs/plugins/")

---

### Post by linuxnovice on 2007-06-05
Hi,

luciferin was right. I click on the beryl settings. I tried berly-manager in the terminal and apparently beryl started up. The thing is my full screen was just white. I used ctrl-alt-(up,down,left,right arrows) to change the desktops but I couldnt see anything. The screen was just white, even though I did see some of the cube graphics. Finally I had to go command line and reboot the system. Any idea?

Thanks for the opera links. It installed beautifully.

Any thoughts on why kate is prompting errors?

---

### Post by plcdfa on 2007-06-05
> **coolbrook said:**
> Did you try loading Opera to a blank page?  Coincidentally I installed it for the first time on Feisty and I noticed that there doesn't appear to be a plug-in for Adobe Flash Player.. either that or I'm completely daft with my attempts to install.  I have to re-install Opera since it can't see any plug-ins at all any more.



Good eye. I didn't notice his signature.

Hey men, what the hell are you talking about? Opera **does** run in KDE. You shouldn't spread such rubbish. (Sorry if I were rude, but that pissed me off.)

---

### Post by Colonel Kilkenny on 2007-06-05
Yeah, of course Opera runs in KDE.

And those BadDevice errors come from xorg.conf as it has wacom tablets defined.
If those errors irritate you (they are harmless) then you could comment every line which has something to with wacom. But remember to backup your old xorg.conf...

This **might** work:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

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
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "int10"
Load "vbe"
load "glx"
load "GLcore"
load "v4l"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
option "CoreKeyboard"
option "XkbRules" "xorg"
option "XkbModel" "pc105"
option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
option "CorePointer"
option "Device" "/dev/input/mice"
option "Protocol" "ImPS/2"
option "ZAxisMapping" "4 5"
option "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "stylus"
#option "Device" "/dev/input/wacom"
#option "Type" "stylus"
#option "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "eraser"
#option "Device" "/dev/input/wacom"
#option "Type" "eraser"
#option "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "cursor"
#option "Device" "/dev/input/wacom"
#option "Type" "cursor"
#option "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

Section "Device"
identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
boardname "i810"
busid "PCI:0:2:0"
driver "i810"
screen 0
EndSection

Section "Monitor"
identifier "Generic Monitor"
modelname "Custom 1"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
depth 24
virtual 1280 1024
modes "1280x960@60" "1280x1024@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
#InputDevice "stylus" "SendCoreEvents"
#InputDevice "cursor" "SendCoreEvents"
#InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection
Section "device" # 
identifier "device1"
boardname "i810"
busid "PCI:0:2:0"
driver "i810"
screen 1
EndSection
Section "screen" # 
identifier "screen1"
device "device1"
defaultdepth 24
monitor "monitor1"
EndSection
Section "monitor" # 
identifier "monitor1"
gamma 1.0
EndSection
Section "ServerFlags"
EndSection
```

edit. And wine is used like this in console.
"wine /media/cdrom/Setup.exe" would start Setup.exe from cdrom (the directory might be different in different systems)

---

### Post by linuxnovice on 2007-06-05
Sorry if I am missing something here....What is the xorg.conf file in the previous post for?

---

### Post by Outrunner on 2007-06-05
> **linuxnovice said:**
> Sorry if I am missing something here....What is the xorg.conf file in the previous post for?

You can use it instead of your current one to get rid of the errors while running kate.

---

### Post by linuxnovice on 2007-06-05
Hi,
Thanks for that. I did that, but the errors are still there. I am posting both the old and new xorg files for reference:

The new one (currently in use):
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

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
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "int10"
Load "vbe"
load "glx"
load "GLcore"
load "v4l"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
option "CoreKeyboard"
option "XkbRules" "xorg"
option "XkbModel" "pc105"
option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
option "CorePointer"
option "Device" "/dev/input/mice"
option "Protocol" "ImPS/2"
option "ZAxisMapping" "4 5"
option "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "stylus"
#option "Device" "/dev/input/wacom"
#option "Type" "stylus"
#option "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "eraser"
#option "Device" "/dev/input/wacom"
#option "Type" "eraser"
#option "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "cursor"
#option "Device" "/dev/input/wacom"
#option "Type" "cursor"
#option "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

Section "Device"
identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
boardname "i810"
busid "PCI:0:2:0"
driver "i810"
screen 0
EndSection

Section "Monitor"
identifier "Generic Monitor"
modelname "Custom 1"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
depth 24
virtual 1280 1024
modes "1280x960@60" "1280x1024@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
#InputDevice "stylus" "SendCoreEvents"
#InputDevice "cursor" "SendCoreEvents"
#InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection
Section "device" # 
identifier "device1"
boardname "i810"
busid "PCI:0:2:0"
driver "i810"
screen 1
EndSection
Section "screen" # 
identifier "screen1"
device "device1"
defaultdepth 24
monitor "monitor1"
EndSection
Section "monitor" # 
identifier "monitor1"
gamma 1.0
EndSection
Section "ServerFlags"
EndSection

The old one:
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
  identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1280 1024
    modes "1280x960@60" "1280x1024@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 1
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection


Any ideas?

---

### Post by overdrank on 2007-06-05
> **plcdfa said:**
> Hey men, what the hell are you talking about? Opera **does** run in KDE. You shouldn't spread such rubbish. (Sorry if I were rude, but that pissed me off.)

I apologize for any hard feelings I may have caused. I was only going off when I tried to install opera on Kubuntu it said that Opera was not compatible with KDE. I stand corrected.

---

### Post by Colonel Kilkenny on 2007-06-06
> **linuxnovice said:**
> Hi,
Thanks for that. I did that, but the errors are still there. I am posting both the old and new xorg files for reference:
...
Any ideas?
Did you restart X server? It needs to be restarted after changes.
Pressing ctrl-alt-backspace should do the trick.

---

### Post by plcdfa on 2007-06-06
> **overdrank said:**
> I apologize for any hard feelings I may have caused. I was only going off when I tried to install opera on Kubuntu it said that Opera was not compatible with KDE. I stand corrected.
When did you got those messages? I really dont't want to go off topic,I just didn't have any of those, and I'm curious now. For me Opera only said some of its shortcuts won't work in KDE.

---

### Post by Happy_Man on 2007-06-06
Yeah, whenever I used to open a terminal and start something, those bad opcode errors showed up. I fixed it a while ago, and they really are harmless. No need to worry about them. :)

---

