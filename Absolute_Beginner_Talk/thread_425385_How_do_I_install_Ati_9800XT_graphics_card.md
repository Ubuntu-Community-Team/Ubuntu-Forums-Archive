---
title: "How do I install Ati 9800XT graphics card?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-04-27
Hi

I've looked at various postings and got various ideas on how best to install an ATi 9800XT card. There appears to be a lot of unresolved problems, particuarly performance. I have the card running now in Fiesty, it flickers at 60Hz but works. I can't change this in System/Preferences/Screen Resolution so assume I have a simple default vga driver at present. I have not attempted to install an alternative driver but would like to know if there is any chance of success in getting the card to work to it's full potential. (Works fine in XP system)

I have been to AMD/ATi website[ www.ati.amd.com/products/catalyst/linux.html#6]("www.ati.amd.com/products/catalyst/linux.html#6")
and they say they have a driver for linux.

They say that all cards 9500 and above are supported. They offer the following for linux:

Quote:
Driver packages are available for XFree86 versions 4.1, 4.2, and 4.3, as well as X.Org 6.8.
Has anybody tried these? Do they work? Which one do you use in Ubuntu?

Thanks

---

### Post by LuisGMarine on 2007-04-27
You can follow this guide here [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") on how to install the ATI drivers for your card.  I personally have nvidia, but most people I have helped who are trying to get their ATI drivers install I refer them to that guide and they say it works like a charm.  Maybe someone else here on the forum can vouch for the authenticity and reliance of that guide?

-LuisGMarine

---

### Post by freebird54 on 2007-04-27
The settings for your card can be altered to give better performance than you have now, without getting the drivers.  IF you get the drivers, get them from the repositories - they are quite reasonably up to date if you don't have the latest X series card.

The secrets of settings are in your /etc/X11/xorg.conf file.  It can be directly edited, or you can run a program to help you set it up better than the default did.  Either way - first do this:  Open an Applications->Accessories->Terminal and put in the following:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_070427
```

which will create a backup file just in case.  :)

The method I recommend is to run:

```
sudo dpkg-reconfigure xserver-xorg
```

after reading the walk-through found here:

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

Hope this helps!

PS - yes, as you can see in my sig, I use an ATI card  :)

PPS.  If you have more questions, or decide to get the drivers anyway, ask!

---

### Post by germaike on 2007-04-27
hey,


i just installed ubuntu 7.04 on my desktop pc. I have a ati 9800 serie and i tried to install the ati drivers. Then i restarted my desktop and i got a black screen and my Screen gives a pop-up that the mode is not supported! I'm a beginner in linux so i don't know what the do next? Can anyone help me with this?

i did this first
Quote:
# Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
# Start text mode installer and install Ubuntu/Kubuntu.
# Finish Install and reboot.
# Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
# Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
# Update loaded modules.
sudo depmod -a
# Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Then i followed the instructions on this tutorial where i used method 2.
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide]("http://wiki.cchtml.com/index.php/Ubu...allation_Guide")

thx

germaike

---

### Post by bwallum on 2007-04-27
Luis, it seems germaike (below) tried the route you proposed. Do you have any insight into what may have gone wrong? I would like to avoid my gui blacking out. I am going to try your route, just looking for a mine detector!

Regards, Bob

---

### Post by bwallum on 2007-04-27
freebird (above) offered this link [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html) It looks as though it directly applies to your scenario. I'm printing out a copy just in case! Regards, Bob

---

### Post by bwallum on 2007-04-27
A big hand to you Ubuntu boys n gals! There is a very simple way to set up an Ati card 9800XT (and possibly others from 9550)

Go to System/Administration/Restricted Drivers Manager
Enable the ATI accelerated graphics driver and reboot when prompted.

Thats it! A card icon appears top right. Click on it and reminds you that it is a proprietory driver unsupported by Ubuntu. Works a treat so far.

Thanks all! A very pleasant experience all round.

Kind Regards
Bob

---

### Post by kittyhawk63 on 2007-04-27
> **bwallum said:**
> A big hand to you Ubuntu boys n gals! There is a very simple way to set up an Ati card 9800XT (and possibly others from 9550)
Go to System/Administration/Restricted Drivers Manager
Enable the ATI accelerated graphics driver and reboot when prompted.
Thats it! A card icon appears top right. Click on it and reminds you that it is a proprietory driver unsupported by Ubuntu. Works a treat so far.
Thanks all! A very pleasant experience all round.
Kind Regards
Bob

Now if something was that simple for the ATI Radeon 9200 SE. What worked in Dapper ,with some tweaking, has not worked in Edgy or Feisty.

Still experiencing screen freezes and black screens every 20 minutes or less.
Tired of ctrl+alt+backspacing or rebooting.  :confused:
kh

---

### Post by kittyhawk63 on 2007-04-27
> **bwallum said:**
> A big hand to you Ubuntu boys n gals! There is a very simple way to set up an Ati card 9800XT (and possibly others from 9550)
Go to System/Administration/Restricted Drivers Manager
Enable the ATI accelerated graphics driver and reboot when prompted.
Thats it! A card icon appears top right. Click on it and reminds you that it is a proprietory driver unsupported by Ubuntu. Works a treat so far.
Thanks all! A very pleasant experience all round.
Kind Regards
Bob

Now if something was that simple for the ATI Radeon 9200 SE. What worked in Dapper, with some tweaking, has not worked in Edgy or Feisty.

Still experiencing screen freezes and black screens every 20 minutes or less.
Tired of ctrl+alt+backspacing or rebooting.  :confused:

Edit: I couldn't even click "Submit Reply" before I had a black screen. Grrrr
kh

---

### Post by germaike on 2007-04-27
ok, he will install the driver then but can you use the desktop effects? i tried it before and those effects didn't work!. I'm looking for a driver install were the effects stay and your card is perfectly installed

thx for looking into it bwallum

---

### Post by thegreenman on 2007-04-27
desktop effects wont work with the restricted drivers, i saw no improvement over the open source drivers on my 9600 xt.  

I ended up reverting to the open source drivers to get the desktop effects working again. 
When you get tired of the restricted drivers do a search here for revert to back open source drivers and you'll find out how to do it.

---

### Post by freebird54 on 2007-04-27
It is still possible to get the effects workiing with the proprietary drivers, but you have to use Xgl to do so.  This can break some other things that otherwise work.  Your choice - effects, or games  :)  Lots of how tos for Edgy, and as far as I can tell, they work for Feisty too.

Myself - I reverted to open source, but my ATI chipset is old enough to be supported (9550 Radeon - RV350 AS).

Kh - which setup are you on right now?  If you post your xorg.conf, I might be able to spot the trouble and suggest an alternative.

---

### Post by kittyhawk63 on 2007-04-27
.

---

### Post by kittyhawk63 on 2007-04-27
> **freebird54 said:**
> It is still possible to get the effects workiing with the proprietary drivers, but you have to use Xgl to do so.  This can break some other things that otherwise work.  Your choice - effects, or games  :)  Lots of how tos for Edgy, and as far as I can tell, they work for Feisty too.

Myself - I reverted to open source, but my ATI chipset is old enough to be supported (9550 Radeon - RV350 AS).

Kh - which setup are you on right now?  If you post your xorg.conf, I might be able to spot the trouble and suggest an alternative.

I am on Feisty. Sorry for the delay. I was working on fixing this dad burn contraption. This is the longest that the screen has not crashed or become frozen. Either one has happened between five and ten minutes every time that I have booted for the past two months . BUT, this time, It has been over 5 hours. I dare not blink or sneeze. 
To let you know what I have done so far on this install.
I uncommented all debs.
I placed "noaip" at the end of each kernel line in /etc/X11/xorg.conf
I changed "ATI" to "Vesa" in xorg.conf.
I installed Thunderbird 1.5. Totem Xine, and a couple more programs via Automatix2.

kh
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
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "record"
    Load    "v4l"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104k"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Compaq FS740"
    Driver        "vesa"
    BusID        "PCI:0:3:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Compaq FS740"
    Option        "DPMS"
    HorizSync    30-70
    VertRefresh    50-120
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Compaq FS740"
    Monitor        "Compaq FS740"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

#I am not sure if there is special spacing between the words in the following lines.
Section "Extensions"
    Option     "Composite"  "Disable"
EndSection

Section "ServerFlags"
    Option    "AIGLX"   "off"
EndSection

---

### Post by freebird54 on 2007-04-28
Off the top of my head (sorry for slow - sleepy!) your difficulty may well be that the monitor and video entries have the same identifier.  Everything else looks pretty much OK, except a couple of things needed for fglrx drivers only - and should be the other way around for anything else (enable).

I attach what I would use for this, including the entries for 'ati' driver - whch I wil show bolded here.  If needed, I'll post up the version I use for fglrx drivers.  here's the 'ati' version:

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
Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "v4l"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104k"
Option "XkbLayout" "us"
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
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
[B]Identifier "ATI 9200SE"
Driver "ati"
Option          "EnablePageFlip" "true"
Option          "RenderAccel" "true"
Option          "ColorTiling" "on"
Option          "AccelMethod" "XAA"
Option          "XAANoOffscreenPixmaps" "on"
#Option         "AGPFastWrite" "on"
#Option         "AGPMode" "4"
Option          "AGPSize" "32"
BusID "PCI:0:3:0"[/B]
EndSection

Section "Monitor"
Identifier "Compaq FS740"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-120
EndSection

Section "Screen"
Identifier "Default Screen"
**Device "ATI 9200SE"**
Monitor "Compaq FS740"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
**Option          "AIGLX" "true"**
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

#I am not sure if there is special spacing between the words in the following lines.
[B]Section "Extensions"
Option "Composite" "Enable"
EndSection[/B]

```

Hope this helps.  If not, I can post the equivalent fglrx version for you.  :)

---

### Post by germaike on 2007-04-28
luckely i tried to install my drivers first. so yesterday i got angry and just reinstalled ubuntu from the top. Now i'm gonna wait a while for an update or something, or a working driver. Now i mentioned it, is there a driver coming that will work??

greetz

---

