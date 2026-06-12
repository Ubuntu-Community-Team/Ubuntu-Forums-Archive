---
title: "Minor Prob - resolution madness - ATI"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by freebird54 on 2007-04-01
I have an oddball thing happening here.  First, a little background.

I have another hard drive around, and I decided to install Edgy a second time, set it up similarly to my main system, and use it for testing 'ideas' and software before deciding to add it to the main system.  So I installed (no probs), and blacklisted ipv6 (again) and installed fglrx (from Envy this time - it seemed to work when it was the FIRST thing I tried).

However, when it was done I had only refresh rates from 43-60, and resolution from 640x480 to 1024x768 available.  Not good enough.  So I dived into xorg.conf to start fixing things.  5 or 6 console 'shutdown -r now' episodes later, I had better choices - but TOO MANY of them.  **Where does the System->Preferences->Screen Resolution get its numbers??**

It scares me - now it shows values that I am sure exceed the capability of the monitor to display - like so:

```
2048 x 1536
1920 x 1440
1800 x 1440
1600 x 1200     etc etc

```
and the refresh rate show from **43 - 90**.  The monitor is capable for **50-160** refresh, 1600 x 1200 max, and 1280 x 1024 x 85Hz 'best'.  I LIKE my monitor :) - and I want it to keep looking good...so I don't like those higher choices around.

There are NO references to resolutions in xorg.conf - If I added them, would it pay any attention?

Thanks - if you have any idea....

---

### Post by ajmorris on 2007-04-01
> **freebird54 said:**
> I have an oddball thing happening here.  First, a little background.

I have another hard drive around, and I decided to install Edgy a second time, set it up similarly to my main system, and use it for testing 'ideas' and software before deciding to add it to the main system.  So I installed (no probs), and blacklisted ipv6 (again) and installed fglrx (from Envy this time - it seemed to work when it was the FIRST thing I tried).

However, when it was done I had only refresh rates from 43-60, and resolution from 640x480 to 1024x768 available.  Not good enough.  So I dived into xorg.conf to start fixing things.  5 or 6 console 'shutdown -r now' episodes later, I had better choices - but TOO MANY of them.  **Where does the System->Preferences->Screen Resolution get its numbers??**

It scares me - now it shows values that I am sure exceed the capability of the monitor to display - like so:

```
2048 x 1536
1920 x 1440
1800 x 1440
1600 x 1200     etc etc

```
and the refresh rate show from **43 - 90**.  The monitor is capable for **50-160** refresh, 1600 x 1200 max, and 1280 x 1024 x 85Hz 'best'.  I LIKE my monitor :) - and I want it to keep looking good...so I don't like those higher choices around.

There are NO references to resolutions in xorg.conf - If I added them, would it pay any attention?

Thanks - if you have any idea....


You should have something like this in /etc/X11/xorg.conf :


Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Intergrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

You can change them there.

---

### Post by freebird54 on 2007-04-01
I used to think so too - but it has come up with all these high values without ANYTHING being specfied in xorg.conf (see below)

```
Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

It also bother me that, despite HorizSync and VertRefresh being specified in the monitor section:

```
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

```

it shows 43 and 47 Hz as options - the monitor's range is from 50Hz and up.

Well, I guess I'll try to add in all the SubSection entries, and see if it helps... thanks!

---

### Post by ajmorris on 2007-04-01
> **freebird54 said:**
> I used to think so too - but it has come up with all these high values without ANYTHING being specfied in xorg.conf (see below)

```
Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

It also bother me that, despite HorizSync and VertRefresh being specified in the monitor section:

```
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

```

it shows 43 and 47 Hz as options - the monitor's range is from 50Hz and up.

Well, I guess I'll try to add in all the SubSection entries, and see if it helps... thanks!

Could it be your ati drivers?

---

### Post by freebird54 on 2007-04-01
It could be - but I'd hate to back them out again!

```
freebird@nest:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)

```

```
freebird@nest:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1475 frames in 5.0 seconds = 355.000 FPS
1820 frames in 5.0 seconds = 364.000 FPS
1826 frames in 5.0 seconds = 365.200 FPS
```
 

```
freebird@nest:~$ glxgears -printfps
1317 frames in 5.0 seconds = 263.260 FPS
1314 frames in 5.0 seconds = 262.783 FPS
1320 frames in 5.0 seconds = 263.983 FPS
```

I had similar problems the first time I set up Ubuntu - in that I couldn't get any high enough numbers in the graphic resolution settings - even though they were in the xorg.conf  -  but that went away with one of the many edits and additions I did getting fglrx and Beryl going.  Oh well - it *IS* a minor problem - *IF* no-one uses this machine and gets curious!

---

### Post by ajmorris on 2007-04-01
> **freebird54 said:**
> It could be - but I'd hate to back them out again!

```
freebird@nest:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)

```

```
freebird@nest:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1475 frames in 5.0 seconds = 355.000 FPS
1820 frames in 5.0 seconds = 364.000 FPS
1826 frames in 5.0 seconds = 365.200 FPS
```
 

```
freebird@nest:~$ glxgears -printfps
1317 frames in 5.0 seconds = 263.260 FPS
1314 frames in 5.0 seconds = 262.783 FPS
1320 frames in 5.0 seconds = 263.983 FPS
```

I had similar problems the first time I set up Ubuntu - in that I couldn't get any high enough numbers in the graphic resolution settings - even though they were in the xorg.conf  -  but that went away with one of the many edits and additions I did getting fglrx and Beryl going.  Oh well - it *IS* a minor problem - *IF* no-one uses this machine and gets curious!

have you tried an xserver reconfigure? (sudo dpkg-reconfigure xserver-xorg)

---

### Post by freebird54 on 2007-04-01
OK - reran dpkg-reconfigure - but now I have to add in all the 'extra' goodies for ATI to work right (like AIGLX off, and FBDev on and and).

Let you know when I get it done - and if it worked!

---

### Post by freebird54 on 2007-04-01
Well - it's enough better to call it **RESOLVED **I guess - BUT

It **STILL** has refresh rates lower than the monitor specs call for.

It **STILL** has unused resolutions that are NOT in the xorg.conf.

BUT  - it  ***DID*** remove the scary ones like 2048 x 1440 from the System menu at least - so I can let people use it now!

Thanks for the reminders - I ran it so many times the first time around I forgot to allow for **THAT** being the fix for the resolution mess!

---

