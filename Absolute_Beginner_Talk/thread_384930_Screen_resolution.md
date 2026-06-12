---
title: "Screen resolution"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-03-15
Hi,
Please can u help me?

I understood i would resolve my res prob by adding 2 lines of monitor spec to my xorg.config.

This is my monitor spec

Horizontal scan range 30 kHz to 96 kHz
Vertical scan range 48 Hz to 120 Hz
+
Optimal preset resolution 1024 x 768 at 75 Hz or 85 Hz
Highest preset resolution 1600 x 1200 at 75 Hz
Highest capable resolution 1600 x 1200 at 75 Hz

This is how xorg.configt looks  with the 2 lines inserted. It hasn't worked ?



Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "ULTRASCANP99"
Option "DPMS"
HorizSync 30-96
VertRefresh 48-120
Modeline "1024x768@85" 100.94 1024 1056 1432 1464 768 782 793 807
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "ULTRASCANP99"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
EndSection

---

### Post by chewearn on 2007-03-15
You forgot to say exactly what resolution problem you faced.  Cannot activate 1280x1024?  What error message you see?

---

### Post by nnjond on 2007-03-15
Contrary to the Ubuntu scrn res aplet, my monitor tells me the present res is 60hz.

---

### Post by nnjond on 2007-03-15
No error messages. I can't alter the screen res from the gui which claims

1080x1024@ 86hz

---

### Post by scxtt on 2007-03-15
remove the "Modeline" ...

---

### Post by nnjond on 2007-03-15
Have removed all of the line begining;

"Modeline..."

But the gui srcn prefs remains imutable at 1280x1024 @86Hz

---

### Post by scxtt on 2007-03-15
what resolution do you want?  if you're ONLY getting 1280x1024 (and not 1600x1200) it's because you don't have 1600x1200 as a part of "Modes" ...

---

### Post by nnjond on 2007-03-15
Evidently my Optimal preset resolution 1024 x 768 at 75 Hz or 85 Hz. This is what i want.

---

### Post by scxtt on 2007-03-15
then remove "1280x1024" from all the "Modes" in the file ... you'd really only need to make it look like:

SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection

---

