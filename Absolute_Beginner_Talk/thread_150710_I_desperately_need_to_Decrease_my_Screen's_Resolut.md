---
title: "I desperately need to Decrease my Screen's Resolution...?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-26
Hello ALL !!!

I would like to know how can I decrease my Screen Resolution...?

From the Menu, I select:

1 "System Preferencces\Screen Resolution"

2. Under "Default Settings", the "Resolution" option's List includes ONLY "640x480"...

I need to change it to 800x600...

Please Help...

...Everything is SOOO BIG...

Thanks in advance.

---

### Post by Perfect Storm on 2006-03-26
Try with
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dvarsam on 2006-03-26
[QUOTE=Artificial Intelligence]Try with
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

And whick Xserver Driver should I select?

My Video Card's brand is "Asus V9520 Magic (N-vidia Series)".

What should I select?

Thanks.

---

### Post by Perfect Storm on 2006-03-26
If you installed nvidia drivers you'll see nvidia, if you havn't installed nvidia driver yet then choose nv

---

### Post by dvarsam on 2006-03-26
I just selected the "nv" - probably for "NVIDIA"...

But then I am asked the following:

&#9474; The X server configuration file associates your video card with a name    &#9474;
 &#9474; that you may provide.  This is usually the vendor or brand name followed  &#9474;
 &#9474; by the model name, e.g., "3Dfx Voodoo3" or "ATI Rage Fury Maxx".          &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Enter an identifier for your video card.                                  &#9474;
 &#9474;                                                                           &#9474;
 &#9474; NVIDIA Corporation NV34 [GeForce FX 5200]______________

What should I type instead of "NVIDIA Corporation NV34 [GeForce FX 5200]"?

My eyes are seeing "night sky stars" man...

I will turn blind in no time...

Thanks.

---

### Post by dvarsam on 2006-03-26
I performed a search in "Synaptic", for "nvidia" & found that:

I have already pre-installed on my Ubuntu the "nvidia-kernel-common".

All I could find (to be relevant), is the "nvidia-settings"...

Is this what I need to install?

Thanks.

---

### Post by Perfect Storm on 2006-03-26
You'll better do this in non-X (write down the commands or print them out).

Your card have been detected properly a quick search on google shows that your card uses GF FX 5200

---

### Post by Perfect Storm on 2006-03-26
[QUOTE=dvarsam]I performed a search in "Synaptic", for "nvidia" & found that:

I have already pre-installed on my Ubuntu the "nvidia-kernel-common".

All I could find (to be relevant), is the "nvidia-settings"...

Is this what I need to install?

Thanks.[/QUOTE]


```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/nvidiasettings.desktop
```

add:
>  [Desktop Entry]
Name=Nvidia Control Center
Comment=Nvidia Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;


save and exit.

reboot.

---

### Post by dvarsam on 2006-03-26
Dear "Artificial Intelligence",

I tried what you said & nothings works...

Any other suggestions?

I went again at "System\Preferences\Screen Resolution"...

And still I ONLY have as an option "640x480".

All this happened because I put as an intermediary between my Graphic's Card & My Screen a D-Link's 2-Port KVM Switch...

This is a plug&play switch to access 2 PC's through 1 Console...

E.g. To be working with 2 boxes simultaneously but with 1 Monitor Screen, 1 mouse & 1 keyboard...

This product supports resolution up to 2048x1536... so it should not be a problem...

I currenly am running 2 PC's: 1 Ubuntu & 1 Windows (from 1 Screen, 1 Keyboard & 1 mouse)...

On the Windows side, I can increase Resolution up to 1600x1200...

On the Ubuntu side, I am left ONLY with 640x480 (@#$^@#^#)...

Can anybody help me "beat" the Windows Machine resolution?

The Windows machine is a Processor 233MHz & the Ubuntu is a 2.4GHz machine...

So I should be able to perform better on My Ubuntu... (its hardware is much much newer man...).

Please Help...

Thanks.

---

### Post by Perfect Storm on 2006-03-26
Do you have your monitor manual? How does your xorg.conf looks like?

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by dvarsam on 2006-03-26
At the same time I noticed the following:

Sometimes my Mouse's plug does not connect very well to the D-Link KVM Switch...

So if for some reason I loose my mouse's connection & I replug the wire in:

1. In the Windows PC, it re-activates the Mouse movement & my mouse works fine again...

2. In the Ubuntu PC, it does NOT re-activate the Mouse movement & I am left without a mouse until I reboot...

I guess that needs improvement in Ubuntu...

But, anyway, Ubuntu is still my Favorite OS!!!


Can anybody help me solve this Resolution's "pain"?

Thanks.

---

### Post by dvarsam on 2006-03-26
Thanks for your reply!!!

As you requested, my "/etc/X11/xorg.conf" file, looks like this:


root@ubuntu:/etc/X11# cat xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "BL 151AX"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "BL 151AX"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection


I haven't Tampered it in any way....
So, hopefully it should look brand new...

After installing "Nvidia" I went on the Menu & selected "Applications\System Tools\Nvidia Control Center".

I looked around in there, but there was NO section to adjust the Screen's Resolution...

Thanks again!

---

### Post by xXx 0wn3d xXx on 2006-03-26
[QUOTE=dvarsam]At the same time I noticed the following:

Sometimes my Mouse's plug does not connect very well to the D-Link KVM Switch...

So if for some reason I loose my mouse's connection & I replug the wire in:

1. In the Windows PC, it re-activates the Mouse movement & my mouse works fine again...

2. In the Ubuntu PC, it does NOT re-activate the Mouse movement & I am left without a mouse until I reboot...

I guess that needs improvement in Ubuntu...

But, anyway, Ubuntu is still my Favorite OS!!!


Can anybody help me solve this Resolution's "pain"?

Thanks.[/QUOTE]


I also have this problem with my ATi cards. I don't know how to fix it either :( I also feel your pain.

---

### Post by Perfect Storm on 2006-03-26
Try check these howtos: 

[http://ubuntuforums.org/showthread.php?t=76387](http://ubuntuforums.org/showthread.php?t=76387)

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Find this in your xorg
> 
Section "Monitor"
Identifier "BL 151AX"
Option "DPMS"
EndSection

change it to:

Section "Monitor"
Identifier "BL 151AX"
Option "DPMS"
HorizSync XX - XX
VertRefresh XX - XX
EndSection

where the X's is the number you can find in you monitor manual.
Warning: Wrong numbers can cause damage to your monitor so better double and trible check.

Reboot.

---

### Post by xXx 0wn3d xXx on 2006-03-26
[QUOTE=MasterChief1234]I also have this problem with my ATi cards. I don't know how to fix it either :( I also feel your pain.[/QUOTE]
After a reinstall and editing my xorg file, I fixed it :) Even with the vesa drivers, the display looks great !

---

### Post by Perfect Storm on 2006-03-26
[QUOTE=MasterChief1234]After a reinstall and editing my xorg file, I fixed it :) Even with the vesa drivers, the display looks great ![/QUOTE]


You might check this for ATI cards: [http://doc.gwos.org/index.php/3D_Graphic_Cards](http://doc.gwos.org/index.php/3D_Graphic_Cards)

Also:
[http://ubuntuforums.org/showthread.php?t=75378&highlight=ATI](http://ubuntuforums.org/showthread.php?t=75378&highlight=ATI)

---

### Post by dvarsam on 2006-03-26
I can not find the Monitor's manual...

It is in my Parent's house...

So, I will try to search the Internet.

My model is "Philips Brilliance 151AX WideViewing Angle"

Hopefully Iwill find some stuff...

Thanks.

---

### Post by dvarsam on 2006-03-26
I visited the site:
[http://www.dooyoo.co.uk/tft-monitor/philips-brilliance-151ax/prices/](http://www.dooyoo.co.uk/tft-monitor/philips-brilliance-151ax/prices/)

And downloaded the "Product Details" PDF Document...

Some of its data, probably relevant to what I need, are the following:

Display:
Diagonal Size                   15"
Viewable Size                   15.1"
Dot Pitch / Pixel Pitch         0.3 mm
Max Resolution                  1024 x 768 / 75 Hz
Colour support                  24-bit (16.7 million colours)
Max Sync Rate (V x H)           75 Hz x 60 kHz
Factory Preset Resolution Modes 640 x 350 / 70 Hz ¦ 720 x 400 / 70 Hz ¦ 640 x 480 / 60 Hz
                                ¦ 640 x 480 / 67 Hz ¦ 640 x 480 / 73 Hz ¦ 640 x 480 / 75
                                Hz ¦ 800 x 600 / 75 Hz ¦ 800 x 600 / 60 Hz ¦ 800 x 600 /
                                72 Hz ¦ 832 x 624 / 75 Hz ¦ 1024 x 768 / 60 Hz ¦ 1024 x
                               768 / 70 Hz ¦ 1024 x 768 / 75 Hz
Front Panel Controls Power on/off, brightness, OSD-position, select
On-Screen Controls   Colour temperature selection
Interface            VGA (HD-15)

Image:
Image Colour Temperature 9300K, 6550K, adjustable
Image Aspect Ratio       4:3
Image Contrast Ratio     250:1
Image Max H-View Angle   +80 / -80
Image Max V-View Angle   +55 / -55

> 
change it to:

Section "Monitor"
Identifier "BL 151AX"
Option "DPMS"
HorizSync XX - XX
VertRefresh XX - XX
EndSection

where the X's is the number you can find in you monitor manual.
Warning: Wrong numbers can cause damage to your monitor so better double and trible check.
Then Reboot...


Can anybody figure the right #'s from what I have provided, or should I check elsewhere...?

Since there is a chance to damage the screen, I need a second opinion on this...

Thanks.

---

### Post by dvarsam on 2006-03-26
I managed to FIX this!!!

I was playing around with the "dpkg-reconfigure xserver-xorg" to FIX my Ubuntu PC's resolution & I ended up NOT being able to Boot into My Ubuntu....

I had ended up destroying my GDM interface...

So, I had to repost my NEWLY created problem...


To SOLVE it, I performed this:

1. I booted fror the Ubuntu Live CD.

2. Inside the "/mnt", I performed a "mkdir linux_os"

3. I then performed a "mount -t ext3 /dev/sda1 /mnt/linux_os"

4. I then moved to the "/etc/X11" folder

5. I did a "cp /etc/X11/xorg.conf /mnt/linux_os/etc/X11/"

6. Then I finally was able to Reboot my Ubuntu from the Hard Drive!


Strangely enough, I could then do this:


From the Menu, I select:

1 "System Preferencces\Screen Resolution"

2. Under "Default Settings", the "Resolution" option's List includes:

    a. "640x480",
    b. "800x600", &
    c. "1024x768".

Basically It included ALL my Monitor's capabilities!!!

I then decided to switch it to  1024x768...

AND EVERYTHING works perfect as before!!!!

Thank you ALL for your help!!!

---

