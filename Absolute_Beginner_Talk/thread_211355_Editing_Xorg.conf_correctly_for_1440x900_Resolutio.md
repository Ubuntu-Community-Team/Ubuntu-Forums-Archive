---
title: "Editing Xorg.conf correctly for 1440x900 Resolution"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by tregarton on 2006-07-08
Right I've done all that's been mentioned in the past. I still only get the 1600x1200 as a NEW option. I've attached by xorg.conf file for you all to view and hopefully help me!

Section "Monitor"
Identifier "Acer AL1916W"
HorizSync 24.0 - 80.0
VertRefresh 56.0 - 60.0
Option "DPMS"
Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 945G Integrated Graphics Controller"
Monitor "Acer AL1916W"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900"
EndSubSection
EndSection

---

### Post by evilghost on 2006-07-08
You are using a modeline however you are not referencing it.  You must use:

DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900**@60**"
EndSubSection

---

