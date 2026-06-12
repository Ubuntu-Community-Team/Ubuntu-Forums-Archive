---
title: "Dual Monitors Problem"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by angus-higgins on 2007-01-27
I am using an ATi Radeon 9800 Pro, dual headed graphics card, and I am trying to set up dual monitors on it as this will finish off the setting up of my Ubuntu install, and make it possible for me to really use Ubuntu as my main operating system (compliments to all who have worked on it as I really think it is great).

I have been working on this for ages, and I hope someone can help.

I have my primary monitor (19" 1280*1024) running on the VGA (analogue) output of the graphics card, and my secondary (15" 1024*768) running on the DVI output of the graphics card, and I would like to have them arranged so that the secondary is on the left of the primary, at the bottom of it.

I managed to get this to work (sort of) in Fedora Core 6, but I like Ubuntu 6.06 LTS better, and I am trying to get this dual monitor system to work.

The relevant parts of my xorg.conf file are:

```
Section "Device"
Identifier "ATI Technologies, Inc. R350 AH [Radeon 9800 SE]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. R350 AH [Radeon 9800 SE] (Secondary)"
Driver "ati"
BusID "PCI:1:0:1"
EndSection

Section "Monitor"
Identifier "BenQ T903"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection

Section "Monitor"
Identifier "Fujitsu Siemens B15"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. R350 AH [Radeon 9800 SE]"
Monitor "BenQ T903"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

Section "Screen"
Identifier "Secondary Screen"
Device "ATI Technologies, Inc. R350 AH [Radeon 9800 SE] (Secondary)"
Monitor "Fujitsu Siemens B15"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"Section "Device"
Identifier "ATI Technologies, Inc. R350 AH [Radeon 9800 SE]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. R350 AH [Radeon 9800 SE] (Secondary)"
Driver "ati"
BusID "PCI:1:0:1"
EndSection

Section "Monitor"
Identifier "BenQ T903"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection

Section "Monitor"
Identifier "Fujitsu Siemens B15"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. R350 AH [Radeon 9800 SE]"
Monitor "BenQ T903"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

Section "Screen"
Identifier "Secondary Screen"
Device "ATI Technologies, Inc. R350 AH [Radeon 9800 SE] (Secondary)"
Monitor "Fujitsu Siemens B15"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
Screen "Secondary Screen" RightOf "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
Option "xinerama" "true"
Option "Default Layout"
EndSection

Section "DRI"
Mode 0666
EndSection
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
Screen "Secondary Screen" RightOf "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
Option "xinerama" "true"
Option "Default Layout"
EndSection

Section "DRI"
Mode 0666
EndSection
```

Can anyone give me some help with the file as currently I am running with the 15" monitor cloning the 19" monitor (in the same resolution [1280*1024], which is out of range, and hence the monitor turns off after a few minutes; and given that it has the speakers that I use on, it is rather annoying).

I appreciate any help, thanks in advance.

Angus Higgins

---

### Post by orb9220 on 2007-01-27
> so that the secondary is on the left of the primary

Screen "Secondary Screen" RightOf "Default Screen"

change to 

Screen "Secondary Screen" LeftOf "Default Screen"

See if that works

---

### Post by angus-higgins on 2007-01-27
> **orb9220 said:**
> Screen "Secondary Screen" RightOf "Default Screen"

change to 

Screen "Secondary Screen" LeftOf "Default Screen"

See if that works

Sorry, I meant I want the Secondary screen on the right of the Primary screen. :p

I can't even get the monitors to do any form of dual monitors, the smaller one just stays in clone mode.

Angus Higgins

---

### Post by angus-higgins on 2007-01-28
Can anyone help?

I am getting pretty annoyed about this because my speakers are on my secondary monitor which has to be turned off for much of the time, so it is annoying when I want to watch a video, or listen to music.

Thanks in advance.

Angus Higgins

---

### Post by gumbald on 2007-01-28
Have you tried this thread? [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

(I'm also from OcUK forums btw, greetings :))

---

### Post by angus-higgins on 2007-01-28
> **gumbald said:**
> Have you tried this thread? [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

(I'm also from OcUK forums btw, greetings :))

Yeah :p

(Nice to see a familiar face; especially as you are from my region [well I think so]).

I tried that yesterday, and it didn't work well, just crashing XServer.

I have my Xorg.0.log file up:

[[Link]]("http://angus-higgins.com/misc/Xorg.0.log")

Does that help anyone?

Angus Higgins

---

### Post by Xappe on 2007-01-28
I'm not sure xinerama can handle a united desktop with different resolutions. you should look into merged frame buffer instead, I think (mergedfb). That at least worked for my radeon 9600 pro.

Something like this:

[http://www.ubuntuforums.org/showthread.php?t=162363]("http://www.ubuntuforums.org/showthread.php?t=162363")

---

