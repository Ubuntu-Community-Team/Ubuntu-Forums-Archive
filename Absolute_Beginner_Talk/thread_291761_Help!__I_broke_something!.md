---
title: "Help!  I broke something!"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by pastorjay on 2006-11-02
I messed somehting up trying to get Beryl to work.  I know it is a matter of just editing something that I told to not load "NV" 

All iget get at boot up is "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

Ok, so what am I looking for, and what can I do to fix it?  HELP!  There are other issues as well, and I will list them as we go:

1. Fixed the X server issue
2. Fixed the resolution problem
3. Now working on sound... why can't I hear anything?  Where do i look?

---

### Post by taurus on 2006-11-02
Boot your Ubuntu to recovery mode from GRUB menu.  Then at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Reboot and see if you can get into X again...

---

### Post by pastorjay on 2006-11-02
did not help at all... grrr!

---

### Post by taurus on 2006-11-02
Post your /etc/X11/xorg.conf here then!!!

```
more /etc/X11/xorg.conf
```

p.s.  Remember, it's "nv" not "NV" since Linux/Unix is case sensitive...

---

### Post by pastorjay on 2006-11-02
Thanks for all your help!

sudo nano /etc/default/linux-restricted-modules-common
Add "nv" at the bottom. (no quotes)

That was what I had edited and configured incorrectly.  I have the desktop back now, but my resolution options are ony 640x480, 800x600, and 1024x768.  This is a laptop with 1920x1200 native.  I believe I messed it up when I reconfigured the xserver thing you told me about up top.
So, next issue is: how do I get my resolutions back?

---

### Post by BillGod on 2006-11-02
you can try just running sudo gedit /etc/X11/xorg.conf and adding the resolution you want under depth 24

---

### Post by taurus on 2006-11-02
You didn't get 1920x1200 when you ran that command?

---

### Post by pastorjay on 2006-11-02
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc14"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Cardnvidia 7900gs"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Cardnvidia 7900gs"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by pastorjay on 2006-11-02
that is what I have now.  I may have messed up a bunch of stuff when I did the: dpkg-reconfigure xserver-xorg

Anyways, is there a way to tell it to reconfigure everything back to the original?  I am hoping I did not mess a bunch of things up.

---

### Post by pastorjay on 2006-11-03
Geesh, I messed up a bunch O stuff!  Resolution is fixed, thanks to you all.  Now, my sound is still not working.  I relly messed this up good!

---

### Post by Drakkor on 2006-11-03
Are you at a point were you can just wipe all of it,and re-install ??

---

### Post by pastorjay on 2006-11-03
Well, I could, and this is the first install I have ever done... been using it all week now.  Is there a way to tell the xserver to reconfigure all of the devices?  I would rather not re-install, but if I have messed it up bad, I could....

All I wanted was Beryl installed...geesh!

---

### Post by Drakkor on 2006-11-03
I have found that it is prudent to make a backup... I have two drives,one windows,one ubuntu,and make a regular backup of my whole ubuntu drive in windows with acronis true image (I cheat,lol),but that way if I screw up 
Ubuntu, I can just restore my backup,and everything is just like I had it...
before the catastrophe,lol :p

---

### Post by pastorjay on 2006-11-03
I usually do the same... with acronis.  But I had not gottenthe install quite all the way done.  I should have still don it!

SO, is there a way to reset that xserver file?

---

### Post by halitus87 on 2006-11-03
if u run the old sudo dpkg -recon bla

if u just hit enter and click ok (while paying attention to what is said)
it should reconfigure it self  its prety good with its detection

oh and i would like to say thanks to the guy what said dpkg reconfigure as it fixed my very simmilar problem

oh and did u recently change any hardware?? or just the file??

either way it should save over it again u do run it as sudo heh??

---

### Post by pastorjay on 2006-11-03
> **halitus87 said:**
> if u run the old sudo dpkg -recon bla

if u just hit enter and click ok (while paying attention to what is said)
it should reconfigure it self  its prety good with its detection

oh and i would like to say thanks to the guy what said dpkg reconfigure as it fixed my very simmilar problem

oh and did u recently change any hardware?? or just the file??

either way it should save over it again u do run it as sudo heh??

well, I will try this is just a few moments.  Hopefully I do not break anyting else!  Thanks for all the help!  And no, there were no changes to the hardware.  I was trying some things to get Beryl to work, and I edited a file that I shoul dnot have edited.

---

