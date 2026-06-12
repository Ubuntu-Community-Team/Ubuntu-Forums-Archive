---
title: "Games launch, then fall asleep and must be killed"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by kizmet_x on 2008-01-24
I have an annoying problem with my 32-bit gutsy. Half the time, I can boot my computer and launch my games, they come up like they are supposed to. The other half of the time, as soon as I launch them they immediately stay on a black screen and must be killed to get rid of the window. I have tried giving them ample time to load if for some reason the computer is backed up, it just stays locked.

On a quick system monitor check, it shows around 5% on each core used, and around 150mb out of 2g of ram used. The resources are there, for some reason they system is not using them. When I go to the processes tab, it says they are sleeping. It shows all my processes as sleeping in fact. I am new to ubuntu and I dont know if it is normal to show everything in the processes tab is sleeping.

I checked the power management settings. It is set to lock the computer after 30 minutes of inactivity. This shouldnt be a factor, since I usually launch the games right after a quick email check and a little bit of surfing.

Anyone ever come across anything like this? Thanks in advance.

---

### Post by RomeReactor on 2008-01-24
Hi. What games are you trying to run? does this happen only with games? what video card do you have? please open a terminal (Applications->Accessories->Terminal) and post the output of these commands:
```
sudo lshw -C display
```
and:
```
glxinfo | grep rendering
```

If you have desktop effects on, try disabling them and see if the games run then.

---

### Post by CCNA_student on 2008-01-24
That happened to me when I did not have the proprietary drivers for my ATI video card installed. Go to System>Administration>Restricted Drivers Manager to check.

---

### Post by kizmet_x on 2008-01-24
It seems to only happen with games. It happened with a previous install, only with wine on that install.

 sudo lshw -C display

   *-display               
       description: VGA compatible controller
       product: G80 [GeForce 8800 GTS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

glxinfo | grep rendering
direct rendering: Yes

---

### Post by kizmet_x on 2008-01-24
> **CCNA_student said:**
> That happened to me when I did not have the proprietary drivers for my ATI video card installed. Go to System>Administration>Restricted Drivers Manager to check.
It shows my drivers are installed. On this boot my games do work however.

---

### Post by RomeReactor on 2008-01-24
Try running the games from the terminal and see if they leave any error messages there. Are all those games using Wine?

---

### Post by kizmet_x on 2008-01-24
> **RomeReactor said:**
> Try running the games from the terminal and see if they leave any error messages there. Are all those games using Wine?
No, they are all native games. Frozen bubble, freeciv, saurbraten, pingus,wesnoth, lincity, etc.
Let me reboot and see if they are giving me trouble.

EDIT: On reboot, it wouldnt launch wesnoth. Tried in terminal, this is what happened.
wesnoth
Battle for Wesnoth v1.2.6
Started on Thu Jan 24 22:34:21 2008

started game: 2939785776

Got there and stopped.

---

### Post by kizmet_x on 2008-01-24
When trying to launch Wormux, it seems to freeze upon loading the content.

wormux
o Reading personal config file
=== Wormux version 0.7.9
=== Authors: Lawrence AZZOUG, Anthony CARRE, Laurent DEFERT SIMONNEAU, Jean-Christophe DUBERGA, Matthieu FERTRE, Sebastien GONZALVE, Reiner HERRMANN, Renaud LOTTIAUX, Yannig PERRE, Olivie SERRES, Victor STINNER
=== Website: [http://www.wormux.org](http://www.wormux.org)

Wormux version 0.7.9, Copyright (C) 2001-2006 Wormux Team
Wormux comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions.

Read COPYING file for details.

[ Run game ]
o Load teams: workraveteam, gnuteam, tuxteam, phpteam, thunderbirdteam, konqiteam, firefoxteam, spipteam, wilberteam, oooteam, nupikteam, snortteam, beastieteam
o Load maps: arbre, desert, banquise, araignee, easterisland, qingqong, grenouilles, electronik, noel, wildwestdv, prehistorik, cowland, goodandevil, aquarium, battlenight, hell, pirates, champignon, catacombes, cheese, vulcano, monkeybubbleworld, leafs, paradis, halloween, island, space

EDIT: On Pingus, it gives a parser error.
pingus
Welcome to Pingus 0.7.1!
========================
data path:               /usr/games/../share/games/pingus/data/
language:                English
font encoding:           iso-8859-1
sound support:           enabled
music support:           enabled
resolution:              800x600
fullscreen:              disabled

SavegameManager: Parser problem: Couldn't open file '/home/ross/.pingus/savegames/savegames.scm'.

---

### Post by RomeReactor on 2008-01-24
Do you have desktop effects on? post the output of:
```
cat /etc/X11/xorg.conf
```

---

### Post by kizmet_x on 2008-01-24
No effects on.

cat /etc/X11/xorg.conf
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
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTS]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8800 GTS]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
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
EndSection
Section "Module"
        Load            "glx"
EndSection

---

### Post by RomeReactor on 2008-01-24
Your xorg.conf looks OK. Is your user account the only one on the system? Try deleting the **.pingus** folder:
```
rm -R ~/.pingus
```
and run it again. I'm not sure, but this could be a permissions issue.

---

### Post by kizmet_x on 2008-01-25
Removing pingus with the terminal didnt work. So I removed it with the add/remove programs tab. Something weird happened though. After I did that, I went and checked the system monitor again. There were like 6 instances of lincity running, all sleeping. As soon as I killed all 6, the system went and immediately launced wesnoth.

Could this be a bottleneck issue?

---

