---
title: "How do I change the refresh rate?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Jimpdx on 2007-03-01
My display adapter supports 1280x1024 resolution @75 Hz, but my monitor doesn't.  I need to change one or the other, and I've decided that lowering the refresh rate to 60 Hz is the way to go.  So how do I do this?  I found a page with instructions late last night and bookmarked it, but now it's inaccessible.  

I just have to say that this seems to be one area where M$ does something better than Gnome/Linux.  Changing these values in XP is fast and simple.  Something to ponder for developers of Ubuntu.

---

### Post by invalid on 2007-03-01
```
gksudo gedit /etc/X11/xorg.conf
```
You will find the values here which you can modify.
Restart X for them to take effect.

---

### Post by benfindlay on 2007-03-01
you should just be able to go into your display properties in Ststem>>Preferences>>Screen Resolution and change it to the values you want to use

Alternatively type ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure your X setup, choosing medium when you get the option between simple, medium adn advanced. In there you can set the available display ranges and choose your optimum I believe!

Hope this helps!

---

### Post by lolwhites on 2007-03-02
Where in the xorg.conf file do I find the refresh rate? I want to go up from 50 to 75 Hz on my new monitor, but the System>>Preferences>>Screen Resolution only goes up to 50Hz.

---

### Post by invalid on 2007-03-02
> **lolwhites said:**
> Where in the xorg.conf file do I find the refresh rate? I want to go up from 50 to 75 Hz on my new monitor, but the System>>Preferences>>Screen Resolution only goes up to 50Hz.

These belong to the monitor section.
For reference, here is what mine looks like:
```
Section "Monitor"
	Identifier	"Hanns.G HX19"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	56-75
EndSection
```

---

### Post by Songwind on 2007-03-02
If you want to set the refresh rate for a particular resolution, you can add _XX where XX is the refresh rate to the resolution listed in the devices.  I can post an example from my own xorg.conf when I get home if that doesn't make sense.

---

### Post by lolwhites on 2007-03-03
My monitor section says:

> Section "Monitor"
    Identifier     "VE510b"
    HorizSync       30.0 - 62.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

What should the figures be for a 75 Hz refresh rate?

---

### Post by Songwind on 2007-03-03
> **lolwhites said:**
> My monitor section says:
What should the figures be for a 75 Hz refresh rate?

I'm not sure how X decides what refresh to use with what resolution.  My old monitor was wearing out so everything looked fuzzy at 85Hz so I modified the Screen section like this:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 6600 0"
    Monitor        "CTX 19"
    DefaultDepth    24
    Option         "UseDisplayDevice" "CRT"
    ...
    SubSection     "Display"
        Depth       24
        Modes       **"1280x1024_75"** "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

The bold code tells it to use 75Hz no matter what refresh the monitor should be able to use at 1280X1024.

---

