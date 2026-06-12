---
title: "imac G3"
date: 2010-07-02
forum: Apple Hardware Users
---

### Post by dzon65 on 2010-07-02
I've been trying for ages to get any distro on this imac G3 (512Mb ram,80Gb hd).None,really none of them worked.Started with karmic,all the way down to 6.06.That is,as well the full as the minimal iso.None of them worked.Or,they stopped halfway the installation,the cd was spitten out after some secs,the login didn't work......whatever.Karmic (cli) was the one that actually got me to command lines only to prompt me with invalid verification.Tried everything I found (forum,threads,google...,nothing).
Then there's debian.Tried the full lenny as well as the businesscard edition.Both installed.The full booting on.....nothing (black screen) and the businesscard didn't recognize ANY of the commands.I'd have to count them but I'm pretty sure I've downloaded and burned (2X speed) like 12 cd's.
I promised this girl I'd get her machine running (her parents can't buy her a new pc),but I'm beginning to feel I'l have to disappoint her.
Pretty sure I tried every thread on installing linux on a imac by now,unless I missed something.So,does anyone know about an exellent how-to?
And if not,does this imac (it's one of the youngest of its kind) support tiger?
Thanks in advance.
Kind regards,J.

---

### Post by linuxopjemac on 2010-07-02
[http://mac.linux.be/content/linux-mint-lxde-debian-50-ppc-fact](http://mac.linux.be/content/linux-mint-lxde-debian-50-ppc-fact)
and then after you installed everything you report yourself in the forums there and I will help you getting X to work.

---

### Post by dzon65 on 2010-07-02
Okay,will do.Alvast bedankt.
Regards,J.

---

### Post by dzon65 on 2010-07-02
Didn't work.Again,black screen on reboot,like all other debian installs.Doesn't matter what I do,it always ends up like this.Don't get it.

---

### Post by linuxopjemac on 2010-07-02
You have to read what I said. You need help to get X to work. Go to [http://mac.linux.be/phpBB3](http://mac.linux.be/phpBB3) and make a thread in PowerPC -> Linux Mint. I will help to get X working.

---

### Post by linuxopjemac on 2010-07-02
[This ]("http://www.silvioto.it/images/acceso1_1024.jpg")will be the result.

---

### Post by dzon65 on 2010-07-02
It took far over two hours to get it installed.I know the xorg.conf has to edited.Only one problem,nano /etc/X11/xorg.conf?Well,there's no cursor,can't edit anything in there.
Gonna have a go as follows,setting up a simple lxde system.Install the debian lenny base system.
apt-get install sudo (i'm used to sudo)
sudo apt-get update
sudo apt-get install xorg synaptic lxde
sudo nano /etc/X11/xorg.conf and edit the file.(provided there's a cursor)
something like this perhaps?
Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
EndSection

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

That should do the trick,wright?

---

### Post by dzon65 on 2010-07-02
I finally managed to install debian lxde on this imac G3.BUT.It's taking aaaaages to get to the desktop or do whatever.I was wondering,there were two pc 133 ramcards under the hood.Total being 512Mb ram.Are those the right cards or could sd do a better job?
Oh,and I guess the xorg.conf file could use better settings as well.The boot screen is split,one half being normal black,the bottom half being pink-reddish.
But the main issue being the vvvvveeeeeeeeerrrrrrrrryyyyyyyyyy low "speed".

---

### Post by linuxopjemac on 2010-07-02
what is the exact model?

[http://everymac.com](http://everymac.com)

```
cat /proc/cpuinfo
```

Did you use the Mint installer script ?

---

### Post by dzon65 on 2010-07-03
Goodmorning,Linuxopjemac.
It's a hmmm slot(?) loading M5521 model.And no,didn't use the mint installer.Just to save some time.So during install I unchecked all boxes,installed xorg and lxde and edited the xorg.conf.This still took close to an hour (on a pc something like this would take 30-45 minutes).I just wanted to know what's wrong with this mac,fast.The mint setup took me close to three hours.
About that xorg.conf?Weird thing,had to add a bunch of things myself.Here's what I mean,I left the sections and lines I had to add that weren't even there (like HorizSync and VertRefresh).Not sure if I have to change UseFBDEV to ati in the "Device" section though.
But anyhow,something's wrong,I could easily have a meal between login and desktop.Even opening the menu takes a few minutes.

Section "Device" 
Identifier "Configured Video Device" 
BusID "PCI:0:18:0" 
Option "UseFBDev" "true" 
EndSection

Section "Monitor" 

HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen" 

Monitor "Configured Monitor" 
EndSection

Section "Module" 
Disable "glx" 
Disable "dri" 
EndSection

Kind regards,J.

---

### Post by dzon65 on 2010-07-03
After some googling,I found there's quite a few probs getting linux on this model.

---

### Post by linuxopjemac on 2010-07-03
Try this:


```
Section "Monitor"
Identifier "Configured Monitor"
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
#Virtual 1024 768
EndSubSection
EndSection

Section "Module"
Disable "dri"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "intl"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "CCEusecTimeout" "100000"
#Option "UseFBDev" "true"
EndSection

```

---

### Post by linuxopjemac on 2010-07-03
You could also try this one:



```
Section "Files" 
      FontPath   "/usr/share/X11/fonts/misc" 
      FontPath   "/usr/share/X11/cyrillic" 
      FontPath   "/usr/share/X11/100dpi/:unscaled" 
      FontPath   "/usr/share/X11/75dpi/:unscaled" 
      FontPath   "/usr/share/X11/fonts/Type1" 
      FontPath   "/usr/share/X11/fonts/CID" 
      FontPath   "/usr/share/X11/fonts/100dpi" 
      FontPath   "/usr/share/X11/fonts/75dpi" 
      # paths to defoma fonts
      FontPath   "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType" 
      FontPath   "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID" 

Section "Module" 
   Load   "GLcore" 
   Load   "i2c" 
   Load   "bitmap" 
   Load   "ddc" 
   Load   "dri" 
   Load   "extmod" 
   Load   "freetype" 
   Load   "glx" 
   Load   "int10" 
   Load   "type1" 
   Load   "vbe" 
EndSection

Section "InputDevice" 
   Identifier   "Generic Keyboard" 
   Driver      "kbd" 
   Option      "XkbRules"   "xorg" 
   Option      "XkbModel"   "pc104" 
   Option      "XkbLayout"  "us" 
EndSection

Section "InputDevice" 
   Identifier   "Configured Mouse" 
   Driver      "mouse" 
EndSection

Section "Device" 
   Identifier   "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)" 
   Driver      "ati" 
   Option      "UseFBDev"      "true" 
   Option      "AGPMode" "2" 
   Option      "AGPFastWrite" "true" 
EndSection

Section "Monitor" 
   Identifier   "Generic Monitor" 
   Option      "DPMS" 
   HorizSync     60-60
   VertRefresh   75-117
EndSection

Section "Screen" 
   Identifier   "Default Screen" 
   Device      "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)" 
   Monitor      "Generic Monitor" 
   DefaultDepth   24
   SubSection "Display" 
      Depth      1
      Modes      "800x600" "640x480" 
   EndSubSection
   SubSection "Display" 
      Depth      4
      Modes      "800x600" "640x480" 
   EndSubSection
   SubSection "Display" 
      Depth      8
      Modes      "800x600" "640x480" 
   EndSubSection
   SubSection "Display" 
      Depth      15
      Modes      "800x600" "640x480" 
   EndSubSection
   SubSection "Display" 
      Depth      16
      Modes      "800x600" "640x480" 
   EndSubSection
   SubSection "Display" 
      Depth      24
      Modes      "800x600" "640x480" 
   EndSubSection
EndSection

Section "ServerLayout" 
   Identifier   "Default Layout" 
   Screen      "Default Screen" 
   InputDevice   "Generic Keyboard" 
   InputDevice   "Configured Mouse" 
EndSection

Section "DRI" 
   Mode   0666
EndSection
```

---

### Post by dzon65 on 2010-07-03
Lol.The moment I started typing that first repy this morning,I opened a terminal on the mac.I just got the results.!!!!???:D
Xorg and lxpanel are taking the biggest chunk of cpu.Okay,gonna try these configs.I'll let you know.(not sure when though,wouhahaha)

---

### Post by dzon65 on 2010-07-03
Well,the first one didn't work at all.Can't get to login.Gonna give the second one a try later this day.Need a break.
Regards,J.

---

### Post by dzon65 on 2010-07-04
finally,finally managed to install debian on the machine.It needed a huge xorg.conf file but it works.

---

### Post by linuxopjemac on 2010-07-04
congratulations

---

### Post by dzon65 on 2010-07-04
Thanks!Man,went through hell!Did a lot of minimals but never quite one like this one,jeezes.

---

### Post by linuxopjemac on 2010-07-05
Post your working xorg.conf file please.

---

### Post by dzon65 on 2010-07-05
That's strange.I did yesterday.Seems to be gone,along with the thread.Hmmmm
Anyway,here it is.
##mac-ppc-slot-loader-500_600_700-xorg.conf##

# Apple iMac G3/500 (Early 2001 - Flower/Blue) Specs (M7669LL/A*)
# Apple iMac G3/600 SE (Early 2001) Specs (M7680LL/A*)
# Apple iMac G3/700 SE (Summer 2001) Specs (M8510LL/A*)
# ATI Rage 128 Ultra (AGP 2X) video with 16 MB of VRAM.
# Maximum RAM: 1.0 GB (two 512 MB modules).

##mac-ppc-slot-loader-500>600>700-xorg.conf###########

#ref: [http://ubuntuforums.org/showthread.php?t=191080](http://ubuntuforums.org/showthread.php?t=191080)
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# su dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
# Load "i2c"
# Load "bitmap"
# Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "dbe"
Load "glx"
# Load "int10"
# Load "type1"
# Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Driver "ati"
Option "UseFBDev" "false"
Option "SWcursor" "true"
Option "ForcePCIMode" "true"
Option "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
Option "AIGLX" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
################end#####################

---

### Post by hector70john on 2010-07-06
We have three fully running G3 imacs in the office, they're rad,  actually.  Panther totally flies on them.  One of them will become a  file server and phone network (using PhoneValet) in the near future.
________________________

[buy a bikini](http://buyabikini.net)

---

### Post by dzon65 on 2010-07-07
Well,after a couple of days this one gave up.That is.The pram battery's a goner.So,it pretty much works,but the keyboard layout keeps switching and the clock is set to 2003.So,I can acces the internet but no way to acces email or the forum for example.Did some googling and they're pretty cheap (the batteries) but they don't wanna spend it on the rig (?!?!)."They" work in one of the biggest electronical shops in Belgium (go figure).Every once and a while I buy old pc's for 50 euros to play around with and they run like a dream,whether with ubuntu/openbox or slitaz whatever,but noooo.Another machine going to the dump I guess.

---

### Post by linuxopjemac on 2010-07-07
I want to have it, maybe you can send it by post :) I live in the Netherlands.

---

### Post by dzon65 on 2010-07-07
It's not mine.I'm doing this for a girl whose parents are even to damn miserly to buy that battery.Buying the battery myself.Unbelievable.

---

