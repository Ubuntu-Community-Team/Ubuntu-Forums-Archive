---
title: "Got ATI 3D working, but still have this weird problem."
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-02-08
Finally got 3D working! But i'm still having this weird issue. Is there some color settings I don't have right or something? That's two different monitors in the picture. On the right is a CRT, on the left is an LCD.

[img]http://www.ghost9.com/videoproblem.jpg[/img]

---

### Post by BarfBag on 2007-02-08
Does it always look weird like that, or only when you hit the log out button?

---

### Post by -Ghost9- on 2007-02-08
only when i hit the logout button. instead of just darkening things, it distorts all the colors.

---

### Post by BarfBag on 2007-02-08
> **-Ghost9- said:**
> only when i hit the logout button. instead of just darkening things, it distorts all the colors.

I don't think there's a way to fix this.  I have an nVidia card (which have MUCH better drivers) and it does the same thing for me.

---

### Post by -Ghost9- on 2007-02-08
> **BarfBag said:**
> I don't think there's a way to fix this.  I have an nVidia card (which have MUCH better drivers) and it does the same thing for me.

does it affect anything else on your system, or just the logout thing?

---

### Post by -Ghost9- on 2007-02-09
Has anyone else had this problem, or know how to fix it?

---

### Post by -Ghost9- on 2007-02-09
ok. i guess i'm on my own with this one.

---

### Post by shareMenaPeace on 2007-02-09
Please open 
```

gedit /var/log/Xorg.0.log
```

And see if there are any lines beginning with EE or WW and if so post them here.

---

### Post by Sunflower1970 on 2007-02-09
> **-Ghost9- said:**
> Has anyone else had this problem, or know how to fix it?

Yeah, I had that problem...but my screen looked like that all the time:

[[IMG]http://img.photobucket.com/albums/v294/erikak1970/th_00005.jpg[/IMG]](http://img.photobucket.com/albums/v294/erikak1970/00005.jpg)

The only way I was able to correct it was by changing my DVI connector to the analog connector. I was using an nVidia Geforce3 Ti 500 card at the time. I switched out the card to a more powerful one (problem went away with DVI then), and I plunked the old card into an older machine. 

Now, I only get it on closing (the older card & computer using the analog connector), but I'm much happier that my screen isn't like that all the time.

---

### Post by -Ghost9- on 2007-02-09
> **shareMenaPeace said:**
> Please open 
```

gedit /var/log/Xorg.0.log
```

And see if there are any lines beginning with EE or WW and if so post them here.


oh yeah i have lots.

```

(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
```

```
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
```

```

(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
```

```

(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
```

---

### Post by -Ghost9- on 2007-02-09
i tried installing beryl and got this message:( i'm sure it's not good.)

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

