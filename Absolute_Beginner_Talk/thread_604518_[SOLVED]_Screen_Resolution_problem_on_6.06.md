---
title: "[SOLVED] Screen Resolution problem on 6.06"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Bunky on 2007-11-06
I've just installed 6.06 and my screen resolution is stuck at 640x480. I used to using 1280x1024. 640x480 is a little HUGE. I've read a bunch of threads on this and haven't worked out what I'm doing wrong. I am a total noob when it comes to Linux too which is not helping. Any help much appreciated.

---

### Post by overdrank on 2007-11-06
> **Bunky said:**
> I've just installed 6.06 and my screen resolution is stuck at 640x480. I used to using 1280x1024. 640x480 is a little HUGE. I've read a bunch of threads on this and haven't worked out what I'm doing wrong. I am a total noob when it comes to Linux too which is not helping. Any help much appreciated.

HI and welcome, what is the video card you are using? This link may help some
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Paste if you need additional help you could post your xorg with this command ```
cat /etc/X11/xorg.conf
``` in the terminal located under applications, accessories, terminal.

---

### Post by Bunky on 2007-11-06
Thanks for the reply and the welcome. :) I'm scanning the link for info. It's a bit like reading those large print books my gran reads but hopefully I'll find the answer without getting a headache. lol 

How do I find out what video card I have? Also I put that code into Terminal and it said: 

cat: /X11/xorg.conf: No such file or directory

---

### Post by overdrank on 2007-11-06
> **Bunky said:**
> Thanks for the reply and the welcome. :) I'm scanning the link for info. It's a bit like reading those large print books my gran reads but hopefully I'll find the answer without getting a headache. lol 

How do I find out what video card I have? Also I put that code into Terminal and it said: 

cat: /X11/xorg.conf: No such file or directory

HI and you can use the command ```
lspci
``` it will list your video card and make sure in the previous command that is a capital X .:KS

---

### Post by Bunky on 2007-11-06
Thanks. Still the same problem with the first command. The second gave me this:

0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
0000:02:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
0000:02:02.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by juantovarm on 2007-11-06
you could also try this in the terminal 

sudo dpkg-reconfigure xserver-xorg


It will guide you through the reconfiguration of your xserver

---

### Post by overdrank on 2007-11-06
> **Bunky said:**
> Thanks for the reply and the welcome. :) I'm scanning the link for info. It's a bit like reading those large print books my gran reads but hopefully I'll find the answer without getting a headache. lol 

How do I find out what video card I have? Also I put that code into Terminal and it said: 

cat: /X11/xorg.conf: No such file or directory

Hi and yes I screwed the command :oops:   ```
cat /etc/X11/xorg.conf
```
Edit and juantovarm has a good idea

---

### Post by Bunky on 2007-11-06
> **juantovarm said:**
> you could also try this in the terminal 

sudo dpkg-reconfigure xserver-xorg


It will guide you through the reconfiguration of your xserver

It's not letting me type in my password for some reason. I put the code into terminal, press enter and then when I try to type in the password it asks for it doesn't do anything as if my keyboard isn't working.

---

### Post by Bunky on 2007-11-06
> **overdrank said:**
> Hi and yes I screwed the command :oops:   ```
cat /etc/X11/xorg.conf
```

Phew! I thought another thinsg wasn't working. This is what it gives me:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Philips 170B"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
        Monitor         "Philips 170B"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection


---

### Post by overdrank on 2007-11-06
> **Bunky said:**
> It's not letting me type in my password for some reason. I put the code into terminal, press enter and then when I try to type in the password it asks for it doesn't do anything as if my keyboard isn't working.

HI it is taking your password just not showing for security. :)

---

### Post by Bunky on 2007-11-06
> **overdrank said:**
> HI it is taking your password just not showing for security. :)

lol Told you I was a noob. Running through this 'sudo dpkg-reconfigure xserver-xorg'
worked in the end. Just need my eyes to refocus and eveything will be fine.:lolflag:

Thanks so much overdrank and juantovarm for your help. It's really appreciated. :)

---

### Post by overdrank on 2007-11-06
> **Bunky said:**
> lol Told you I was a noob. Running through this 'sudo dpkg-reconfigure xserver-xorg'
worked in the end. Just need my eyes to refocus and eveything will be fine.:lolflag:

Thanks so much overdrank and juantovarm for your help. It's really appreciated. :)

No problem and good luck! please mark the thread solve under the thread tools and have fun! :popcorn:

---

