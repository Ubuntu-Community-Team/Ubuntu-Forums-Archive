---
title: "iMac G5: How to get true 24-bit colors?"
date: 2007-06-03
forum: Apple PPC Users
---

### Post by cerbero on 2007-06-03
Hello. I've just installed Ubuntu as a secondary OS on my Rev. B iMac G5 (17" screen). Everything's been going smoothly installation- and speed-wise (aside from a slight problem at bootup where mouseemu took up almost 100% of the CPU - but that's fixed now) - and now I want to get my monitor to work correctly.

All images look as though the color depth is 16 bits, and not 24 (heavy "banding", etc) - 24 bits being what the X server is configured for and, I think, is using. I read something on this forum about the monitor being 6 bit instead of 8, as more expensive LCDs are, and also found a possible fix for nVidia cards here: [http://ubuntuforums.org/showthread.php?t=303366]("http://ubuntuforums.org/showthread.php?t=303366"). Apparently there's supposed to be a similar option for the 'ati' driver called "Dac6bit", but it doesn't make any difference at all if I put it in my xorg.conf and restart the X server.

Does anyone have a solution for this? Any help at all I would be very grateful for. I'll attach my xorg.conf so you'll have something to work with.

Thanks,
Johan (aka cerbero)

---

### Post by stmiller on 2007-06-03
Hey try adding this option line in your devices section:

Option  "AGPMode"  "4"

---

### Post by cerbero on 2007-06-04
I actually tried that option yesterday (though for a different purpose - it was one of the options mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=462312](http://ubuntuforums.org/showthread.php?t=462312)) - to no avail unfortunately.

---

### Post by tcrroadie on 2007-06-04
Hi cerbero,

Could you please post your Xorg.log.  Located in
```

/var/log/Xorg.0.log
```

The Xorg.log file will help give us some information on what is happening when the xserver starts.  The log tells us what Modules and Options are actually being loaded and how your video card is being configured. 

You may also want to try to find the correct Horizontal and Vertical values for your monitor.  The values entered may be beyond what your monitor supports.  You can also try just omitting the values for testing sake to see what happens.  The xserver will just default to some lower values.  Try 

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection
```

I would also recommend changing the settings in your "Device" section to this. 

```
Section "Device"
        Identifier      "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Driver          "radeon"
        BusID           "PCI:240:16:0"
        Option          "UseFBDev"  "false"
        Option          "AGPMode" "8" 
        Option          "AGPFastWrite" "true"
EndSection
```

Thanks.  :D

---

### Post by maxxum on 2007-06-04
sorry, posted in the wrong thread.

---

### Post by cerbero on 2007-06-05
No luck after making those changes. I'm certain it is the screen 6bit/8bit problem though. Along with the changes you suggested, I also added to my xorg.conf the "Dac6Bit" option which, according to ´man radeon´ "Enables or disables the use of 6 bits per color  component  when in  8  bpp mode (emulates VGA mode).". If you check my attached Xorg.0.log though (sorry - had to compress it to be able to stay within the size limit), you'll see that while the "Dac6Bit" option is accepted and understood, it does not have any effect, as this tidbit pops up at line 387:
```
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
```

I'm not sure how to deal with this at all...

---

### Post by stmiller on 2007-06-05
```

(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[snip]
(--) Depth 24 pixmap format is 32 bpp
```

According to that log, it has loaded 24bit color. Might try commenting out the 

#load "dri"

part for now. I know this kills 3D, but see if that makes any difference. Trying to load all the crazy 3D extensions only complicates things.

I've got a Radeon 9600 on my Powermac G5, though I just use the fbdev driver, with 24bit. The radeon driver was just too buggy for 3D. But I haven't investigated fully. I can post my logs and xorg if that would help.

---

### Post by tcrroadie on 2007-06-05
I was reviewing the radeon manual and found some interesting information about what is supported for certain graphics chips.  Looks like 3D support may not fully be supported for your Radeon 9600.  From the radeon manual. 

>        R300        Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL X1/Z1 (2D only)

       RV350       Radeon 9600PRO/9600SE/9600, M10/M11, FireGL T2 (2D only)

       RV360       Radeon 9600XT (2d only)

> radeon  is  an  Xorg driver for ATI RADEON based video cards.  It contains full support for 8, 15, 16
       and 24 bit pixel depths, dual-head setup, flat panel, hardware 2D acceleration, hardware 3D accelera&#8208;
       tion  ([COLOR="Red"]experimental  on  R300 and R400 series cards[/COLOR]), hardware cursor, XV extension, and the Xinerama
       extension.

stmiller may be on to something here.  Lets keep the driver selection "radeon" and fully disable 3D acceleration and see what happens.  As stmiller mentioned, disable dri and add the Option "NoAccel" to your Device section.  Make it look like this. 

```
Section "Device"
        Identifier      "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Driver          "radeon"
        BusID           "PCI:240:16:0"
        Option          "UseFBDev"  "false"
        Option          "AGPMode" "8" 
        Option          "AGPFastWrite" "true"
        Option          "NoAccel"  "true"
EndSection

```

Please post your Xorg.log again after making this change.  

If your image quality problem still persist, you may also want to try changing your selected driver to "fbdev" or "vesa" to see if there is any difference.  

I would also like to note that my late model ibook G4 has a Radeon 9550 video card, and I have no issues with image quality.  I have all 3D options available for my card enabled and it works and looks great.  I am not sure how similar the 9550 is to the 9600 chip.

---

### Post by cerbero on 2007-06-06
Those options (removing load "dri" and setting NoAccell "true") didn't make any difference I'm afraid. I also tried changing the driver to "fbdev" ("vesa" wouldn't allow the X server to start).
I still think the problem is actually sending the colors in the right format to the monitor though, since if I take a screenshot of my Ubuntu desktop and then view it in OS X, the colors look exactly as they should. I should probably also mention that Beryl runs great on the iMac, and I have all the options of it available - it's just that the colors get banded.

I too have Ubuntu running beautifully on my iBook G4, and that's the reason I installed it on the iMac as well - I wanted a bigger screen and a real mouse & keyboard to play around with it.

---

### Post by tcrroadie on 2007-06-06
Have you tried using a lower resolution such as 1024x768 to see if the problem still persist.  

	```
EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

```

It is good to hear that Beryl is working good for you on your iMac.  After we figure this image problem out, we wil make sure that your xserver "Device" section is configured properly to take full affect of Beryl. 

I'll review your new log later tonight and try to find some more information on what could be causing the problem.  

Keep going, don't give up.  We are making progress here.   :D

---

