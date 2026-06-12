---
title: "Been looking through themes, and alot of stuff is under &quot;Beryl&quot;"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by ericxhall on 2008-03-30
When I had Linux before, I had the whole Kde or Kubuntu thing going on, I'm not really sure what it was. And I am wondering, what this beryl thing is, and how to I install Beryl themes.

---

### Post by Tatty on 2008-03-30
Beryl is now known as Compiz Fusion*

It is a compositing window manager for linux - basically nice eye candy.  (if you come from a windows background, think of it as the linux equivalent of Aero)

Compiz Fusion is installed (but not activated) by default in Ubuntu Gutsy, to turn it on go to "System->Preferences->Appearance".  That will allow you to switch on the basic default Compiz settings for Ubuntu.  

If you want to get more advanced and make it do fancier things then try searching on the forums 

good luck :)

**note: Compiz fusion is actually a combination of two related projects,  Compiz and Beryl, which merged last year*

---

### Post by ericxhall on 2008-03-30
This brings me to another probelm, which i made another thread about before, when i click any radio button besides "None". It says "The Composite extension is not available".
And I downloaded Compiz the other day, so below Extra it says Custom.
any further help bro?

---

### Post by Tatty on 2008-03-30
1. What graphics card do you have?
2. Have you installed the proprietry drivers for your card?

---

### Post by ericxhall on 2008-03-30
I am not sure, it is ATI but I am not totally sure.
and I installed/enabled the restriced drivers?
and would you happen to know anything about how i would get my music directories to look like ~/Music/Artist/Album ....like itunes does it automatically everytime you add something in?

---

### Post by Tatty on 2008-03-30
On the graphics issue:

Open up a terminal and type:
```
glxgears
```

you will see three coloured cogs turning on the screen and every five seconds or so it will output how many frames it has displayed.  If you could get five or so readings of this and then post them here.  This will just act as a confirmer that your drivers are working properly.

Obviously do this when you are not doing anything else on the comp so no other applications slow it down.

On the music issue:

Its down to how you want to manage and organise your music really.  What applications do you use to play / rip your music?  

The software should have some sort of option where you can specify where it should place ripped audio and how it names it.

---

### Post by ericxhall on 2008-03-30
2745 frames in 5.0 seconds = 548.949 FPS
3321 frames in 5.0 seconds = 663.630 FPS
3307 frames in 5.0 seconds = 660.732 FPS
3316 frames in 5.0 seconds = 663.182 FPS
3272 frames in 5.0 seconds = 654.281 FPS

---

### Post by Tatty on 2008-03-30
Ok so your drivers are loaded fine.

**EDIT: actually the FPS looks kind of low, i was readin it wrong when i first read it**
We need to know what card you have:  try running this command:

```
lscpi
```

then post the output here.

I was just browsing over this thread [http://ubuntuforums.org/showthread.php?t=436110]("http://ubuntuforums.org/showthread.php?t=436110")

It suggests :

> **TMulder said:**
> Maybe i'm just too simple. But you may want to try and change:

Section "Extensions"
Option "Composite" "0"
EndSection

to

Section "Extensions"
Option "Composite" "**1**"
EndSection

at the bottom of your xorg.conf

Try doing that.  If it doesnt work then a later post on the thread suggests to try changing the "1" to "Enable"

---

### Post by ericxhall on 2008-03-30
eric@eric-laptop:~$ lscpi
bash: lscpi: command not found

AND

where is xorg.conf
ugh sorry about being such a new jack

---

### Post by Tatty on 2008-03-30
my apologies, there was a typo in the command:

```
lspci
```  - this is basically ls (list) pci (pci devices), so lspci.

xorg.conf is located at /etc/X11/xorg.conf  - make sure you capitalise the X in X11 as linux is case sensitive with file and directory names.

to edit it, you can open it with root privilages with:

```
gksudo gedit /etc/X11/xorg.conf
```

But before you do that, it would be nice to see the output of lspci.  also if you could do:
```
cat /etc/X11/Xorg.conf 
```
and post the output of that so we can have a look at your xorg.conf file.

---

### Post by Cresho on 2008-03-30
[http://www.gnome-look.org/](http://www.gnome-look.org/)

right click on desktop and go into effects. select normal or extra.  after ou get those running, you may want to try open synaptic and install compizconfig-settings-manager.  then you can go into system->preffernce-> and advanced desktop effects.

---

### Post by ericxhall on 2008-03-30
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)


Keep in mind I changed the zero to "Enable"
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection


this suuucks bro. and i appreciate all your help.

---

### Post by Tatty on 2008-03-30
Reading the [ATI linux driver wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"), it suggests running this command after you install the driver:

```
sudo aticonfig --initial
```

Just try it and see what happens.

If that fails try simply uninstalling then resinstalling the driver.  Im getting a bit stumped im afraid... im certain there is an answer to this problem, but finding it is seeming to be a bit tricky

---

