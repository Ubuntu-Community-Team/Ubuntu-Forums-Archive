---
title: "Hardy Max Res Deemed to be 640 x 480?!"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by coolcalt on 2008-04-13
Drivers seem to load ok.   my monitor is an acer AL1916-asd  19¨ LCD, which runs 1200x1024 native

please help me improve my screen real estate.

Xorg.0.log
```
 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.15.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
```

xorg.conf
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by llamakc on 2008-04-13
Please ask this question in the Hardy forum and not here.

[http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)

---

### Post by diablo75 on 2008-04-13
Your xorg.conf contains no details about your monitor at all.

What kind of monitor do you have?

---

### Post by mgmiller on 2008-04-13
This drove me nuts with the hardy beta also.  
Right click Applications
select Edit Menus
In the left hand pane, highlight Applications  > Other
In the right pane look for a screen, monitors, video card thing, I don't remember the exact name.  put a check next to it to enable it.
Close the menu editor
click applications > Other > screen, monitor thingy
See if there is an entry for your specific monitor, if not try generic LCD.
If it's a wide screen, look for the wide screen check box in lower left corner and check it.
You should now be able to select your resolution.

---

