---
title: "Frequent Lock-ups"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Supercross on 2007-03-29
I really really want ubuntu to work for me but no matter what I do it seems I cannot win.  Here is what my problem is: Frequent lock ups are plaguing my ubuntu. I originally thought it was my memory so I ran Memtest86 and it always froze up, however it turns out this was a bug with my mobo (ASUS P4P800) and after I got this cleared up I ram Memtest all night and had 0 errors. Next, I was reading online where installing the i386 kernal resolved hard-locks, tried this and it still locks up. I have the fglrx graphics driver installed for my ATi Radeon 9500. What is weird is before I installed the fglrx driver and I would get a lock-up nothing would respond (keyboard or mouse). However after this graphics driver was updated a lock up would occur and I would still have mouse control but no keyboard control and of course my monitor was locked (eg. screensaver would freeze, movie would freeze, etc). It is weird because my windows install never gives me any errors or lock ups yet you would think a Linux-based OS would be the last thing to lock-up, as it is much less resource intensive. Anyways, I really want to use ubuntu but it is very frustrating to have to push the restart button 10 times a day. Does anyone have any ideas about this problem? I will put my system information below.

P4 2.4 Nortwood on ASUS P4P800
1 GB PC3200
ATi Radeon 9500
Sound Blaster Live!
(Everything running default speeds...no overclocking)

---

### Post by Delvien on 2007-03-29
> **Supercross said:**
> I really really want ubuntu to work for me but no matter what I do it seems I cannot win.  Here is what my problem is: Frequent lock ups are plaguing my ubuntu. I originally thought it was my memory so I ran Memtest86 and it always froze up, however it turns out this was a bug with my mobo (ASUS P4P800) and after I got this cleared up I ram Memtest all night and had 0 errors. Next, I was reading online where installing the i386 kernal resolved hard-locks, tried this and it still locks up. I have the fglrx graphics driver installed for my ATi Radeon 9500. What is weird is before I installed the fglrx driver and I would get a lock-up nothing would respond (keyboard or mouse). However after this graphics driver was updated a lock up would occur and I would still have mouse control but no keyboard control and of course my monitor was locked (eg. screensaver would freeze, movie would freeze, etc). It is weird because my windows install never gives me any errors or lock ups yet you would think a Linux-based OS would be the last thing to lock-up, as it is much less resource intensive. Anyways, I really want to use ubuntu but it is very frustrating to have to push the restart button 10 times a day. Does anyone have any ideas about this problem? I will put my system information below.

P4 2.4 Nortwood on ASUS P4P800
1 GB PC3200
ATi Radeon 9500
Sound Blaster Live!
(Everything running default speeds...no overclocking)

Wall of text ! woot.

Well now. What version of Ubuntu are you using. ?

---

### Post by Supercross on 2007-03-29
Edgy, and I have downloaded and installed all available updates. Also, in case it wasn't obvious in my post, these lock-ups are completely random...some happen when I am doing nothing, others happen when I am browsing on the web, configuring system properties, etc, etc, etc.

---

### Post by Supercross on 2007-03-30
I hate to bump this post but does anyone have any ideas here? Everywhere I read ubuntu is praised as being such a stable OS, yet mine is horrible.

---

### Post by freebird54 on 2007-03-30
Speculation here - but the only lock-ups I ever got were when my drivers were not properly configured.  Can you post the output from the following perhaps - to see if anything video is amiss?

```
cat /etc/X11/xorg.conf
```

```
fglrxinfo
```

With those _ I might be able to spot something...

---

### Post by ushills on 2007-03-30
I too am using edgy and have the same motherboard.  I have had lock ups every other day or so where the screen freezes and nothing works.  I have to turn off the PC at the wall.

How did you resolve/test the motherboard, I used to have crashes with windows also hence the move to Linux.

I am using a brand new SATA HDD so the disk shouldn't be the issue.

---

### Post by Supercross on 2007-03-30
Here are what I get from those two commands:

***cat /etc/X11/xorg.conf***
```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     fgl"/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 51.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

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

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection
```

***fglrxinfo***
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

By the way...my monitor is a Viewsonic 19" Widescreen running at 1440x900. I wonder if it has anything to do with this.

---

### Post by freebird54 on 2007-03-30
The monitor should not DIRECTLY have any effect on things - but I do notice that its capabilities ae not specified in the xorg.conf file.  What sort of refresh rate/ sync does it run?

Anyway - you appear to have the fglrx driver installed correctly, and all I can suggest now is to add a couple of lines to the 'device' section:  Here is mine

```

Section "Monitor"
        Identifier   "Samsung_900iFT"
        **HorizSync    30.0 - 100.0**
        **VertRefresh  50.0 - 160.0**
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Radeon 9550"
        Driver      "fglrx"
        [B]Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"[/B]
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Radeon 9550"
        Monitor    "Samsung_900iFT"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

You will note that bits in bold have no counterparts in your file, and it can't hurt to put them in.  However - the actual numbers for HorizSync and VertRrefresh  ***MUST*** match your actual monitor!!  (monitor damage can result from errors).

The 'options' specified are, I think, the most likely to help.  If video is the problem.  If we're lucky.  If it isn't a BIOS setting on your system...

Give it a try and we'll see :)

---

### Post by Supercross on 2007-04-01
Well oddly enough, after entering those options into my xorg.conf file, I have had 0 lockups. However, now my screensavers do not work, there is just a black screen that appears. Even though this is happening at least nothing is locking up and I will take no screensaver over a lock-up any day.

---

### Post by freebird54 on 2007-04-01
Which screensavers give you trouble?  I ended up with Cosmos, as some of the others came with their own lockup troubles on my system....

---

### Post by johnny4north on 2007-04-01
supercross and uphill u might want to check this link out - [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78288](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78288) you both might have the same problem:( .   thank ubuntu

---

