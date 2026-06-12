---
title: "TV adapter"
date: 2007-06-17
forum: Apple PPC Users
---

### Post by maxmartin on 2007-06-17
I recently purchased a mini VGA adapter for my iBook that converts to RCA and S-Video, but it does not seem like Ubuntu wants to play nice with it. Is there some setting or configuration necessary to use such a device, or will it simply not work?

---

### Post by SoggyCornflake on 2007-06-17
> **maxmartin said:**
> I recently purchased a mini VGA adapter for my iBook that converts to RCA and S-Video, but it does not seem like Ubuntu wants to play nice with it. Is there some setting or configuration necessary to use such a device, or will it simply not work?

How about a maybe?  First I suggest you look under the following link: [URL="https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia"]Supported Ubuntu Multimedia Hardware.
[/URL]
If it is not in that short list, you may still get it to work, but not before a lot of "Googling".

It may be as simple as adding a bit to you xorg.conf file  See this example modification to the xorg.conf:

```
  94	Section "Monitor"
    95		identifier "External Monitor"
    96		vendorname "Plug 'n' Play"
    97		modelname "Plug 'n' Play"
    98		modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
    99		modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
   100		modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
   101		gamma 1.0
   102	        Option "VGA"
   103		#HorizSync 30-82
   104		#VertRefresh 56-75
   105	EndSection
```

That example came from a this link:  [http://pierre.baudu.in/ibook/#xorg.conf]("http://pierre.baudu.in/ibook/#xorg.conf")
This was a debian install, not an Ubuntu install.  However, generally if you can get to work in [debian,]("http://www.debian.org/") you should be able to get it done the same way in Ubuntu.

---

