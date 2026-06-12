---
title: "ATI Mobility M7 7500 gfx card / xgl/compiz/3dacceleration"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by raggit on 2006-08-16
I've been trying and trying to get all this to work to no avail.  I think it may boil down to my graphics card on my t41.  The problem is i go through all these tutorials and go step by step but FGLRXINFO always says i have the mesa drivers.  What can I do to get all this running with the M7 7500 ATI card I have on my thinkpad??

---

### Post by gustl87 on 2006-08-16
use the driver called "ati".

i got the m6 and it works fine after editing the xorg.conf

i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and if your pc starts freezing just edit it:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

#sorry for my bad english.

---

### Post by raggit on 2006-08-17
> **gustl87 said:**
> use the driver called "ati".

i got the m6 and it works fine after editing the xorg.conf

i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and if your pc starts freezing just edit it:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

#sorry for my bad english.

are you using the firegl drivers or the or the " motherboards with ati graphics"?  ie:
ATI Proprietary Linux x86 Display Drivers for XFREE86 / X. Org Version 8.27.10
What repositories if any were used, what upgrades did you use in synaptics package manager etc?

Would it be possible to get you to do a step by step of what you did?  It would be great for future users to know how to do it starting from a fresh install.  The biggest thing about linux is the trials one must go through to get things working.  If you would be able to start with downloading and installing the drivers followed by configuring the xorg.conf i'm sure there would be less of these HELP ME threads.  I look forward to your mini tutorial

---

### Post by gustl87 on 2006-08-17
first of all i am very sorry cause i wrote "ati" and meant "radeon" as it is in the xorg.conf part.

i had a fresh installation of ubuntu dapper.
the os used the driver called "ati" in the xorg.conf after installation was complete.

but the "ati" driver caused my pc (compac evo n410c) freezing sometimes, so i began looking around for an howto fix.

and a few days ago i found this :

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

it is very interesting because the guy has basicaly the same video card.
my m6 (it is nearly the same chip as the mobility 7500 and i think it is the mobility 7000) is named :

"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"

but it is NOT a 9000 chip but an 7000 or 7500.

so the guy's card might probably have been detectes das wrong under linux as mine has been.

then i took the card dealing with the video card from his post and replaced the matching part in my xorg.conf with it.

but after rebooting x couldn't start, so something must have been wrong.

and so i edited it ab bit. i disabled (commented #) everything unneccessary and wrote the name of my video card in the "Identifier" line.

i think that i disabled more neccessary but it works on my machine.

here are the xorg.conf parts:

the one from the website:

```
Section "Device"
        Identifier      "Videocard0"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "AGPMode" "4"
        Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        Option          "RingSize" "4"
        Option          "BufferSize" "2"
        Option          "EnablePageFlip" "true"
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        Option          "RenderAccel" "true"
        Option          "AccelMethod" "XAA" # or XAA, EXA
        Option          "DDCMode"
        Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "true"
        Option          "DynamicClocks" "true"
        Option          "bioshotkeys"   "True"
        Option          "XAANoOffscreenPixmaps" "true"
EndSection 
```

and the edited one:

```
Section "Device"
        Identifier      "[PUT THE OLD NAME OF YOUR CARD HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

i can NOT say if it will work on your pc but it is a try.

you have to write your videocard's name which stands in you xorg.conf right now in the Identifier line in your edited xorg.conf - so you have to keep this line in your new xorg.conf

in the topic you say "xgl" - this is the thing with the 3d-desktop and it is not possible with your card (i think i read this on the project homepage).

edit:
the driver was shipped with my linux distribution so i did nothing to install it - and it runs with open gl on my box

#sorry for my bad english

---

### Post by raggit on 2006-08-17
So you are able to run compiz and other stuff enough to enjoy with that setup>??

---

### Post by gustl87 on 2006-08-17
i don't know "compiz" and i installed it just a minute ago, but it will not start because of "No composite extension".

"blender" runs fine and the "flurry" screensaver too.
when i run "glxgears -printfps" i get around 217 FPS.

---

### Post by raggit on 2006-08-17
I tried that setup and got an error.  I did install the ati drivers but they seemed to add to my problems because my screensaver got extremely slow.  I think when i get home from work i'll start all over and use what ever the default drivers are for ubuntu that made my card work decent/  Only reason I say that is because my benchmark is my screensaver.  On a fresh reinstall of ubuntu screensaver works great, as soon as i install the ati drivers the screensaver runs sllllloooooowwwww

---

### Post by gustl87 on 2006-08-17
then continue using the default driver it is called "ati" (?).

the official driver from the ati homepage just supports the mobility series beginning with the mobility 8500.

the M7 is not supported by the closed source ati driver from the ati homepage.

---

### Post by raggit on 2006-08-17
is there a driver out there that supports the 7500 that I could try>

---

### Post by raggit on 2006-08-17
All problems resolved after following the thread posted below

[http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)

---

