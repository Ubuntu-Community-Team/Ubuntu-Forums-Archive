---
title: "Refresh Rate / 32-bit color questions."
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Enkra on 2006-12-28
First, here is my spec:

Westinghouse LVM-37w3
         - DVI connection
         - Native resolution is @1920x1080
         - Maximum refresh rate at native resolution is 60Hz
EVGA GeForce 7950GX2
         - NVIDIA Driver Version: 1.0-9631

My xorg.conf file:

```
Section "Monitor"
    Identifier     "Westinghouse"
    Option         "DPMS"
    HorizSync      30-81
    VertRefresh    60
    Modeline "1920x1080" 148.5 1920 1976 2008 2200 1080 1083 1085 1125 +Hsync +Vsync
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation [GeForce 7950GX2]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation [GeForce 7950GX2]"
    Monitor        "Westinghouse"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080_60"
    EndSubSection
    SubSection     "Display"
        Depth       32
        Modes      "1920x1080_60"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

The first question is:  at what REFRESH RATE is my moniter running at? Obviously I want it to run at 60Hz and I specificially set it at 60 in xorg.conf file. But once I am in Gnome and look at System -> Preferences -> Screen Resolution, I see 50Hz (and give me option to set to 51Hz, 52Hz) but no 60Hz in sight at all. Lastly, when I go to System Tools -> NVIDIA X Server Settings -> X Server Display Configuration, it says 60Hz. So which one is right? Am I running at 50 or 60?

Also, when I set "DefaultDepth 32" in xorg.conf I get an error message saying there is no support for 32-bit color. But in NVIDIA X Server Settigs, it say I am running at Millions of Colors (32bpp). And there is no 24-bit in sight, just 16bpp and 8pp. So am I running at 24bit or 32bit color?

Thanks in Advance.

---

### Post by The Noble on 2006-12-28
24 bit color _IS_ 32 bit color. I don't remember the exact reason for it, but I think the explanation is that the last 8 bits are filler for "something", although I don't know what that "something" is. I don't know about your refresh rate problem, as I am the same way and haven't bothered to look for the fix/answer.

---

### Post by eXisor on 2006-12-28
I notice you refer to 1920x1080_60 in the screen section, but the modeline is called 1920x1080 (without the _60). 

The first field after the modeline is the name, so you need to match that in the screen setting to use the new modeline.

This explains why you are not getting the 60 mhz refresh rate.

Did you generate the modeline using gtf? ie. 

```
gtf 1920 1080 60
```

or did you use an online modeline generator? I found gtf worked better since it generated a modeline that is within the clock rate range of my monitor. The online generators did not.

Give that a bash and let us know.

---

### Post by Enkra on 2006-12-29
> **eXisor said:**
> I notice you refer to 1920x1080_60 in the screen section, but the modeline is called 1920x1080 (without the _60). 

The first field after the modeline is the name, so you need to match that in the screen setting to use the new modeline.

This explains why you are not getting the 60 mhz refresh rate.

Did you generate the modeline using gtf? ie. 

```
gtf 1920 1080 60
```

or did you use an online modeline generator? I found gtf worked better since it generated a modeline that is within the clock rate range of my monitor. The online generators did not.

Give that a bash and let us know.

I use gft and this is the modeline I get:
```
# 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
```

I use the modeline from "gft" and restart gdm.  NVIDIA X Server Settings now say Auto Detect for both resolution and refresh rate. But System -> Preferences -> System Resolution still say 50Hz @1920x1080.

---

### Post by eXisor on 2006-12-29
Post your new xorg.conf.

---

### Post by Enkra on 2006-12-30
New xorg.conf :

```
Section "Monitor"
    Identifier     "Westinghouse"
    Option         "DPMS"
    HorizSync      30-81
    VertRefresh    60
    # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
    Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation [GeForce 7950GX2]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation [GeForce 7950GX2]"
    Monitor        "Westinghouse"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1920x1080_60.00"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080_60.00"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

---

### Post by eXisor on 2006-12-30
That all looks fine, but you say no go?

I did a google and found a post from a someone setting up his westinghouse in FC xorg. Notice how his modeline is completely different, and how his vertrefresh has a range?

```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Westinghouse"
	ModelName    "LVM-42w2"
	HorizSync    31.5 - 70.0
	VertRefresh  50.0 - 70.0
	ModeLine     "1920x1080" 138.5 1920 1968 2000 2080 1080 1082 1087 1111
	Option	     "dpms"
EndSection

```

Here is the link to his page in case you can glean more info from there... You'll notice he actually gets the modeline from his Xorg.0.log file which is rather cunning, I think. Also notice the Option' 'dpms' line. Perhaps xorg is trying ti use DDC instead? Anyhow, try the dpms setting too.

[http://home.att.net/~Tom.Horsley/easy-linux.html](http://home.att.net/~Tom.Horsley/easy-linux.html)

As you can see he has the LVM-42w2, while you have the 'LVM-32w2', but may hap that won't make too much difference.

Give the above a bash and let us know.

EDIT: If this doesn't work, post your Xorg.0.log file here so we can see what xorg thinks is going on, what it uses and where it fails.

---

### Post by Enkra on 2007-01-01
> **eXisor said:**
> That all looks fine, but you say no go?

I did a google and found a post from a someone setting up his westinghouse in FC xorg. Notice how his modeline is completely different, and how his vertrefresh has a range?

```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Westinghouse"
	ModelName    "LVM-42w2"
	HorizSync    31.5 - 70.0
	VertRefresh  50.0 - 70.0
	ModeLine     "1920x1080" 138.5 1920 1968 2000 2080 1080 1082 1087 1111
	Option	     "dpms"
EndSection

```

Here is the link to his page in case you can glean more info from there... You'll notice he actually gets the modeline from his Xorg.0.log file which is rather cunning, I think. Also notice the Option' 'dpms' line. Perhaps xorg is trying ti use DDC instead? Anyhow, try the dpms setting too.

[http://home.att.net/~Tom.Horsley/easy-linux.html](http://home.att.net/~Tom.Horsley/easy-linux.html)

As you can see he has the LVM-42w2, while you have the 'LVM-32w2', but may hap that won't make too much difference.

Give the above a bash and let us know.

EDIT: If this doesn't work, post your Xorg.0.log file here so we can see what xorg thinks is going on, what it uses and where it fails.

Hmm interesting read. I notice that he used 1920x180@57 instead of 1920x1080_57, does it make a difference?

Also I check my /var/log/Xorg.0.log and my NVIDIA driver doesn't provide the monitor EDID like his does. Here's a section of my Xorg.0.log :
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 7950 GX2 at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.33.08
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7950 GX2 at PCI:5:0:0:
(--) NVIDIA(0):     WDE WestinghouseLVM-37w3 (DFP-1)
(--) NVIDIA(0): WDE WestinghouseLVM-37w3 (DFP-1): 330.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): WDE WestinghouseLVM-37w3 (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(WW) NVIDIA(0): No valid modes for "1920x1080_60.00"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (59, 59); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
```

Notice these lines in the code above?

[B](II) NVIDIA(0): Assigned Display Device: DFP-1
(WW) NVIDIA(0): No valid modes for "1920x1080_60.00"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080[/B]

No valid modes for "1920x1080_60" ???

---

### Post by Enkra on 2007-01-01
Okay I tweak around a bit with my xorg.conf file and got rid of the "no valid modes" error in /var/log/Xorg.0.log file. INVIDIA setting detect my Monitor EDID thru DDC that the HorizSync and VertRefresh is 30-68 and 58-72 respectively; Did gtf again and re-check the modeline.

Here is my new xorg.conf:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "WDE Westinghouse"
    ModelName      "LVM-37w3"
    Option         "DPMS"
    HorizSync      30.0-68.0
    VertRefresh    58.0-72.0
    # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
    Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Geforce 7950 GX2"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080_60"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

And here's the new /var/log/Xorg.0.log file with it:
```
II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 7950 GX2 at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.33.08
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7950 GX2 at PCI:5:0:0:
(--) NVIDIA(0):     WDE WestinghouseLVM-37w3 (DFP-1)
(--) NVIDIA(0): WDE WestinghouseLVM-37w3 (DFP-1): 330.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): WDE WestinghouseLVM-37w3 (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1080_60"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (59, 59); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
``` 

BUT GUESS WHAT!?
System->Preferences->Sreen Resolution still say 50Hz refresh rate.
I think Gnome and Nvidia X Server Setting tool is not on the same page.

LOL! I GIVE UP ](*,)

---

### Post by eXisor on 2007-01-01
No, no, you can't give up before I do.   :)   From the link I provided you can see how tricky it can be, but.... 

One or two things....

1) You forgot to add the .00 at the end of the modeline name in the screen section. 

2) To get the edid values you may need to comment out all the modelines references. Could be the modelines entry is an override of sorts.

If you're still willing, give both those a bash and then post the xorg.conf and xorg.0.log again.

---

### Post by Enkra on 2007-01-01
I tried adding the .00 in the screen section and I get this again:
```
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
```

Furthermore, I check NVIDIA X Server Settings->X Server Display Configuration it recommends this configuration:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    **Option         "metamodes" "nvidia-auto-select"**
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

Keep in mind System->Preferences->Sreen Resolution still say 50Hz refresh rate.

- - - - - - - - - -

So I remove the .00 from both the modeline and screen section and now it's ok again. Here the Xorg.0.log:
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 7950 GX2 at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.33.08
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7950 GX2 at PCI:5:0:0:
(--) NVIDIA(0):     WDE WestinghouseLVM-37w3 (DFP-1)
(--) NVIDIA(0): WDE WestinghouseLVM-37w3 (DFP-1): 330.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): WDE WestinghouseLVM-37w3 (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
[B](II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1080_60"[/B]
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (59, 59); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
```

NVIDIA X Server Settings->X Server Display Configuration now says:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
**    Option         "metamodes" "1920x1080_60 +0+0"**
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

System->Preferences->Screen Resolution still at 50Hz.



A few of questions:
1. What is "metamodes" option? Couldn't find it in the xorg.conf manual maybe it's a Nvidia option?

2. Could the System->Preferences->Screen Resolution  be bugged? My monitor is actually running at 60Hz like Nvidia X Servers Settings say it is, but  Gnome Screen Resolution can't detect it?

---

### Post by eXisor on 2007-01-01
As you say, metamodes is probably an nvidia setting. Also, it wouldn't surprise me at all if the screen resolution app is just plain wrong. 

So it sounds as if you're up and going at 1920x1080_60, which sounds a lot like like mission accomplished.

Now, are you ready to beryl?

---

### Post by Enkra on 2007-01-01
> **eXisor said:**
> Now, are you ready to beryl?

No, not yet! I don't want to open another can of worm. :mrgreen: I think I will mess around with ubuntu for a couple more weeks and learn more about the system.

eXisor, thanks for the help. I am starting to like Linux/Ubuntu more and more. Haven't logged on to  Windows ever since I install this last Tuesday, Plus I learn more in 5 days with Linux/ubuntu than the last 3years with Windows. ;)

---

### Post by c0mput0r on 2008-02-01
so did you ever get the westinghouse lvm-37w3 to ever work in 7.10? I can't. The most I get is 640x480. It detects my HPL2335 just fine because it seems to have a driver for it. Both monitors are connected with dvi out from my 8800 GT which i have nvidia drivers installed for and working. Just get nothing but 640x480 on the westinghouse which sucks because it is the main screen. 

Im trying to convert from windows but it seems the hardware support is just not there even with all new hardware.... sigh... this seems to be the same story every time i have tried linux for the last few years.

---

