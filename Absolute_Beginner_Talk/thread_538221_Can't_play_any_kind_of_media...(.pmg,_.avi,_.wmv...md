---
title: "Can't play any kind of media...(.pmg, .avi, .wmv...nothing works)"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-08-29
*file type above SHOULD be .mpg, not .pmg, but I can't figure out how to edit the topic title/

I'm using Xubuntu 7.04, have installed w32codecs package, and if I'm missing something I should have , please tell me.

I've tried playing these in gxine, totem, mplayer, and VLC. MPlayer just says "Error opening/initializing the selected video_out (v-o) device" or something along those lines, and the rest just quit when I load the files.

It doesn't matter what type of file I play, they all refuse to work ;>.<

Technology hates me, I think.

---

### Post by CowzRule on 2007-08-29
Take a look at the following:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins")

---

### Post by ARandomKid on 2007-08-29
I did everything on there...still doesn't work. ;._.

---

### Post by saj0577 on 2007-08-29
goto Applications/Add-remove and search for gstreamer. That should help for mising multimedia plugins.

Hope it helps
Saj

---

### Post by -SpaZ on 2007-08-29
Might I suggest [EasyUbuntu]("http://easyubuntu.freecontrib.org/")?

---

### Post by Steveway on 2007-08-29
> "Error opening/initializing the selected video_out (v-o) device" 
That is not a codecproblem like the others think.
It is a problem with your choosen videooutput.
You should try another one like XV in the settings of your videoapplication.

---

### Post by -SpaZ on 2007-08-29
> **Steveway said:**
> That is not a codecproblem like the others think.
It is a problem with your choosen videooutput.
You should try another one like XV in the settings of your videoapplication.

Wow.  I feel stupid now.  Thanks for catching our mistake.

---

### Post by st33med on 2007-08-29
VLC, however, can do pretty much any format you can throw at it. download it by this:

```
sudo apt-get install vlc
```

---

### Post by ARandomKid on 2007-08-29
> **Steveway said:**
> That is not a codecproblem like the others think.
It is a problem with your choosen videooutput.
You should try another one like XV in the settings of your videoapplication.

...where exactly would I find this in MPlayer?

All I see ar a bunch of buttons, no "Settings"....nvm I found them. Selected "XV" and it did the same as the rest: quit when playback was initiated.

So...back where I started. and I'm positive this isn't a codec problem, I've installed every codec you guys listed.

---

### Post by ARandomKid on 2007-08-29
> **st33med said:**
> VLC, however, can do pretty much any format you can throw at it. download it by this:

```
sudo apt-get install vlc
```


I tried VLC too, listed above. Same result as the rest, which is why I'm come to the conclusion that either I'm missing something pretty damn huge or technology just hates me. ;>.< I've got about 50 different files of various formats I'm trying, too.

---

### Post by Steveway on 2007-08-29
Try around with the outputs.
XV was just an example, I'm not sure wich would work for you.

---

### Post by st33med on 2007-08-29
Question: what is your video card?

---

### Post by Yizi on 2007-08-29
I had the same problem just installed the code package reboot and it's solved ! ;)

---

### Post by ARandomKid on 2007-08-29
> **st33med said:**
> Question: what is your video card?

00:07.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)


One of those, I'm sure (don't know much about computers)...for future reference, can somebody confirm?

---

### Post by st33med on 2007-08-29
It is the VGA thing...

Never even heard of that company!! How old is your PC?

Not sure if this is in the repoes. Can you try:
```
sudo apt-get install neomagic
```

Actually, can you try:
```
 sudo gedit /etc/X11/xorg.conf 
```

And post it here?

---

### Post by ARandomKid on 2007-08-29
> **st33med said:**
> It is the VGA thing...

Never even heard of that company!! How old is your PC?

Not sure if this is in the repoes. Can you try:
```
sudo apt-get install neomagic
```

Couldn't find the package.

This thing was built from parts that were made when I was 4, maybe 6. I'm 16 now.

Frankly, I'm surprised it's still running as perfect as it is.

---

### Post by st33med on 2007-08-29
Sorry, wrong package.

```
 sudo apt-get install xserver-xorg-video-neomagic 
```

---

### Post by Yizi on 2007-08-29
> **st33med said:**
> VLC, however, can do pretty much any format you can throw at it. download it by this:

```
sudo apt-get install vlc
```

i recommend you install this as well, it woks great specially for .avi movies, its a lot better the QT and other programs.

Thanks for the share :KS

---

### Post by -SpaZ on 2007-08-29
I don't know why people like .avi media anyway, it takes up an obsense amount of space and .mp4 media is just as good.

---

### Post by ARandomKid on 2007-08-29
*xserver-xorg-video-neomagic is already the newest version.*

I **have** installed VLC.

---

### Post by st33med on 2007-08-29
Then post your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by ARandomKid on 2007-08-29
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Neomagic Corporation NM2200 [MagicGraph 256AV]"
        Driver          "neomagic"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Neomagic Corporation NM2200 [MagicGraph 256AV]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by Yizi on 2007-08-29
> **-SpaZ said:**
> I don't know why people like .avi media anyway, it takes up an obsense amount of space and .mp4 media is just as good.

I agree but that's what they do, not everybody have information about formats. :D

---

### Post by st33med on 2007-08-29
Try and add this under device:
```
Option "OverlayMem" "829440"
```

And try again.

---

### Post by ARandomKid on 2007-08-29
That worked. Rather slow, but it's something.

Anything you think I could try as far as speeding it up off the top of your head? If not, it's nothing important.

---

### Post by st33med on 2007-08-29
Not really.

And, are you running off a DVD? That might be what's causing it, because that fix was for DVDs.

---

### Post by st33med on 2007-08-29
Actually, I think I do. Try changing the DefaultDepth to 16

And don't try 3D Desktop. It sucks. Hard.

---

### Post by ARandomKid on 2007-08-29
> **st33med said:**
> Not really.

And, are you running off a DVD? That might be what's causing it, because that fix was for DVDs.

Nope. Just a generic file I found.

DefaultDepth change didn't work. Oh well. Unless you have any other off-the-top-of-your-head solutions, I'll try fixing that later.

---

### Post by st33med on 2007-08-29
[This link]("http://www.linuxquestions.org/hcl/showproduct.php?product=131") is where I found that solution.

---

### Post by ARandomKid on 2007-08-29
> No agpgart or OpenGL or fancy 3D stuff

Oh god. I tried running Boson once when I didn't know about this.

3 seconds per frame. NOT three frames a second. Three seconds per frame.

;x_X Needless to say, it was unplayable. And uninstalled as a result.

Shame. Sounded pretty fun. This is a lot faster than that, though (thankfully)

---

