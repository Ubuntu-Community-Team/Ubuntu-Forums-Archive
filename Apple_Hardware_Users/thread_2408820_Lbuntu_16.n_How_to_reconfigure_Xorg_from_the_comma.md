---
title: "Lbuntu 16.n: How to reconfigure Xorg from the command-line"
date: 2018-12-23
forum: Apple Hardware Users
---

### Post by jharris1993 on 2018-12-23
Note to admins:
This queston may be general enough that you may wish to move it out of the "Apple Hardware" section and place it in a more appropriate place.

System:
Apple iBook G3 (Power PC 32 bit) with 640 megs of memory and an 80 GB hard drive.

Graphics:
ATI Radeon/Rage-128 mobility graphics capable of 1024x768 with a 32 bit color depth.

O/S:
Lbuntu 16.n (LTS) for PowerPC installed from the alternate installer CD, fully updated (via apt-get) as of this instant date.

The system works wonderfully with OS/X Tiger installed.

Information:
I have been having recurring issues getting Lbuntu to install and boot - the subject of a different thread.  Now I can get it to boot using "radeon.modeset=0".

Issue:
After booting, I get an unusable graphical display that looks like it's being viewed through a coarse screen.

Issue:
After getting to a command-line via Alt-F1, I cannot configure the X-server from the command line.  Apparently "dpkg reconfigure" for xorg has been depreciated and appears to do absolutely nothing.  Other postings suggest that the configuration for the xorg xserver is now a graphical utility, depending on a working GUI.

Question:
Given that I *DO NOT* have a working GUI, and only have access to a command line interface, how do I re-configure xorg/xserver on a system running Lbuntu 16.n?

Thanks in advance for any help you can provide.

Jim "JR"

---

### Post by wildmanne39 on 2018-12-23
Hello, you did good, it belongs here!

---

### Post by jharris1993 on 2018-12-23
> **wildmanne39 said:**
> Hello, you did good, it belongs here!


Ok, now how do I fix it? (wink!)

A number of postings scattered around the Web suggest that Ubuntu 16.n and ATI/AMD graphics don't play well together- especially if your graphics card is more than fifteen minutes old. :p

Since I don't know if Lbuntu 18.n exists for the 32 bit PPC platform, I am going to try moving back to 14.n and see how that works.

Jim "JR"

---

### Post by wildmanne39 on 2018-12-23
I am not an expert on ATI but I have a new computer with ATI card and it works great with Ubuntu 18.04 but it does not come in 32bit but lubuntu does, your card should be recognized during install and the correct driver should be installed for it.

---

### Post by vidtek on 2018-12-24
> **jharris1993 said:**
> Note to admins:
This queston may be general enough that you may wish to move it out of the "Apple Hardware" section and place it in a more appropriate place.

System:
Apple iBook G3 (Power PC 32 bit) with 640 megs of memory and an 80 GB hard drive.

Graphics:
ATI Radeon/Rage-128 mobility graphics capable of 1024x768 with a 32 bit color depth.

O/S:
Lbuntu 16.n (LTS) for PowerPC installed from the alternate installer CD, fully updated (via apt-get) as of this instant date.

The system works wonderfully with OS/X Tiger installed.

Information:
I have been having recurring issues getting Lbuntu to install and boot - the subject of a different thread.  Now I can get it to boot using "radeon.modeset=0".

Issue:
After booting, I get an unusable graphical display that looks like it's being viewed through a coarse screen.

Issue:
After getting to a command-line via Alt-F1, I cannot configure the X-server from the command line.  Apparently "dpkg reconfigure" for xorg has been depreciated and appears to do absolutely nothing.  Other postings suggest that the configuration for the xorg xserver is now a graphical utility, depending on a working GUI.

Question:
Given that I *DO NOT* have a working GUI, and only have access to a command line interface, how do I re-configure xorg/xserver on a system running Lbuntu 16.n?

Thanks in advance for any help you can provide.

Jim "JR"

Jim-
Put this in your xorg.conf:

```
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY AVAMP"  # this will be your own source
    HorizSync       15.0 - 81.0            # whatever your hardware supports
    VertRefresh     24.0 - 75.0           #  whatever your hardware supports
    Option         "DPMS"
    Option         "UseEdidDpi" "FALSE"
    Option         "DPI" "100 x 100"
EndSection
```

This will stop the o/s from auto-detecting the wrong refresh rates and will give usable fonts on the login screen.

For resolution you could try this:

```
Section "Screen" 
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    **Option "metamodes" "nvidia-auto-select +0+0 {viewportin=1920x1080, viewportout=1836x1032+42+23}{ ForceCompositionPipeline = On }"**
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The viewport in and viewport out are the critical bits in this snippet of the xorg.conf, it is where you fix the resolution. The pipeline reference does not apply to ATI cards.

Give it a go, just ctrl-alt F4 and enter root password then ```
nano /etc/X11/xorg.conf
```

Tony

---

### Post by jharris1993 on 2018-12-24
Tony,

You said:

```
 **Option "metamodes" "nvidia-auto-select +0+0 {viewportin=1920x1080, viewportout=1836x1032+42+23}{ ForceCompositionPipeline = On }**
```

within your sample xorg.conf file listing.

Is this correct?  My graphics card is an ATI (aty) Radeon/Rage Mobility card and the maximum resolution is 1024x768-32 and my display is the built-in laptop display.

Does this change your suggested xorg.conf? (I suspect so).

Thanks for your help!

Jim "JR"

---

### Post by jharris1993 on 2018-12-24
Note to everyone:

This is all well and good.  If anyone can suggest updates or modifications to my xorg.conf file, I'm glad to receive them.

However, returning to the original question:  Does anyone know how to invoke the xorg configuration process from the command-line?  Is it even ***possible*** now?

Jim "JR"

---

### Post by vidtek on 2018-12-25
> **jharris1993 said:**
> Tony,

You said:

```
 **Option "metamodes" "nvidia-auto-select +0+0 {viewportin=1920x1080, viewportout=1836x1032+42+23}{ ForceCompositionPipeline = On }**
```

within your sample xorg.conf file listing.

Is this correct?  My graphics card is an ATI (aty) Radeon/Rage Mobility card and the maximum resolution is 1024x768-32 and my display is the built-in laptop display.

Does this change your suggested xorg.conf? (I suspect so).

Thanks for your help!

Jim "JR"

Jim,  I would drop the nvidia bit, but I don't know the ati equivalent.  try just leaving it out and doing the viewport entries.

---

### Post by gsahli on 2018-12-25
I suspect the available utilities are used to detect and setup during install, so you're not going to get anything different.
But try 
"sudo dpkg-reconfigure xserver-xorg"
or
"sudo Xorg -configure"
You may have to kill Xorg before the second one.
These ideas from:
[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Configure_X.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Configure_X.html)

---

### Post by jharris1993 on 2018-12-25
Update:

I tried a test install with the earliest 14.04 version, as the live disk produced an awful, but usable, desktop.  Unfortunately I was not able to install from the live CD, because most windows appeared with no internal resources or buttons visible - only the desktop background.

After installing from the 14.04 alternate installer disk, and rebooting the machine, I was given an absolutely blank (black) screen with the ubiquitous purple mouse pointer.

I opened a terminal session (Alt-Ctl-F1), logged in, became root, and started looking for my xorg.conf file.  No luck.  I also tried a "find" (find / -iname xorg* -print) and the same command redirecting output to a file, and it ***did not find*** a simple xorg.conf file.  The Xorg log file showed a lot of defaults being used, things that could not be determined, and general confusion leading up to X throwing up its hands and giving it up as a hopeless effort.  ](*,) #-o

I could, (and will if requested), upload logs, messages, the result of the "find", and whatever else you might wish.

However, I believe that absent a real and working xorg.conf file in /etc/X11, all of this is possibly pointless.  Once a real and potentially reasonable xorg.conf is installed, we can begin really troubleshooting the problem.  Once that's done, I may also be able to export this solution to my 16.04.n installation.

Question:
Can anyone provide a real, hopefully working xorg.conf file - top to bottom - from a working installation on an iBook G3, using the default laptop display, keyboard, and touchpad?

Thanks!

Jim "JR"

p.s. I strongly suspect that this is at the root of my problems with the 16.04.n installation.  This is why I asked how to re-create an xorg.conf.

---

