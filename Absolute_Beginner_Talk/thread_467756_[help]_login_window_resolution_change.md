---
title: "[help] login window resolution change"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by pcandpc on 2007-06-08
Hi,

I'd like to change the screen resolution for
the login window (before the final desktop).

Where do I do this?

I'm using ce 3.2 (christian edition 3.2)

Thanks.

---

### Post by josesanders on 2007-06-08
Try this:

[http://ubuntuforums.org/showthread.php?t=258484&highlight=bootup+screen+resolution](http://ubuntuforums.org/showthread.php?t=258484&highlight=bootup+screen+resolution)

---

### Post by pcandpc on 2007-06-09
Thanks.

I looked at your link and followed the suggestions there,
but still, the login window's resolution appears to be set
at higher resolution than the desktop's (800*600).

---

### Post by josesanders on 2007-06-09
Sorry, my mistake.  The login screen resolution is apparantly set by your xorg.conf.  If you don't want to use any resolutions above 800x600, you can just remove those in the xorg.conf.  What you do is first make sure you backup your current xorg.conf:

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

Then you need to edit it and change the default resolution:

$ sudo gedit /etc/X11/xorg.conf

That will open a text editor.  In the file, you have a section called "Screen" that looks something like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"DELL P991"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection

     :
     :

	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

The first one is the default resolution, so if you want it to be 800x600, I believe you can just change the section corresponding to the default depth (in my case it is 24) to look like this:

```

     :
     :

	SubSection "Display"
		Depth		24
		Modes		"800x600" "1600x1200" "1280x1024" "1024x768" "720x400" "640x480"
	EndSubSection
EndSection
```

The changes will take effect when you restart your xserver.

---

