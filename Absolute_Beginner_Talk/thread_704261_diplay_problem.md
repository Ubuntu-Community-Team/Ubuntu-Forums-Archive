---
title: "diplay problem"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by hoobadoo on 2008-02-22
I have recently installed the ati drivers for my radeon 9800 pro following the various tutorials out there, but now whenever I restart my computer and the login screen is loading all it says is Can not display video mode. I can still log in but I just can't see anything until the after the login screen. I'm using a dell dimension 8300 with a dell monitor model: E152FPb I have attached my xorg.conf if that is any help.

---

### Post by webjames on 2008-02-22
have you installed the radeon drivers? if so you could TRY:

```

Section "Device"
	Identifier  "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver      "radeon"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

```

however i beleive that a 9800 will act like a 9000 as there is no real support for it as yet. i'm sorry i can't be of more help i hope this gets you going in the right direction. if this doesn't work you could install the drivers of the Radeon website, there are guides on how to do this, 

best of luck!

---

### Post by kesman on 2008-02-22
Get Envy from google and install the drivers with it, that's the easiest way.

---

### Post by hoobadoo on 2008-02-23
I downloaded and installed envy and had it install the drivers for me and auto-configure the xorg.conf but I'm still having the same problems. Whenever I try and log on or play any 3D game it just says "cannot display this video mode".

---

### Post by kesman on 2008-02-23
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"      "1024x768"      "800x600"
        EndSubSection
EndSection

```

This is my "Screen" section. I noticed that your's don't have any resolutions defined already. You should add some, with the highest being the native resolution for your screen. Before editing, take a backup of your xorg.conf just in case... After editing, restart your xorg with either ctrl+alt+backspace or in terminal type
```

sudo /etc/init.d/gdm restart

```

If you still get errors, please let me know.

---

