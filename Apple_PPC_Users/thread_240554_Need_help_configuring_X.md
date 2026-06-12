---
title: "Need help configuring X"
date: 2006-08-21
forum: Apple PPC Users
---

### Post by ghstridr on 2006-08-21
I am having one heck of a time getting X configured on a 1Ghz Apple PowerBook G4 with an ATI video chip.
I have spent several hours looking around the net for solutions, including here.
The problem is that X starts, I hear the Ubuntu 'drums', but all I see is a black screen.  I can login and hear the login sound so I know that gdm is running, but I just can't see anything.

I think my main problem is not having the right config for the screen.
When I boot the box in Single user mode, the boot status screen shows the modules being loaded, but the color Ubuntu logo is in all kinds of funky colors.
I am seeing vrefresh out of range error messages in /var/log/Xorg.0.log, but I can't find specs on this display to set this correctly.
I supposedly have a Radeon 9000 Mobility with 64mb of ram in this thing with a 15" screen. Model A1025 is what is printed on the bottom.

---

### Post by avtolle on 2006-08-21
OK, after you log in and get the blank screen, get to a terminal (Alt+Ctrl+F1), at command line type "sudo dpkg-reconfigure xserver-xorg" (without the quotes), answer the questions (usually the default is what you want), then input at the appropriate time your graphics card, if it isn't identified, when finish, type (I think) "reboot", and see if that helps. Otherwise, you will need to edit your xorg.conf file. Let's try the first option, though, as it seems to me to be somewhat easier to do. Post back with questions.

---

### Post by ghstridr on 2006-08-21
Sorry, that didn't do it.  I can't get to a console screen, I have boot into single-user mode to access a prompt.  Alt+Ctrl+F1-F5 get me a funny white screen with black lines across it.
I did run reconfigure and I still don't know what to put for the monitor, it obviously is auto-detecting it incorrectly.
Does any one know the monitor specs to be used with a Powerbook G4 15" lcd screen?

---

### Post by avtolle on 2006-08-21
I have the same display ( I think); the applicable portion of my /etc/X11/xorg.config file follows:     ```

     [LEFT]Section "Device"
    Identifier    "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
    Driver        "ati"
    BusID        "PCI:0:16:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Apple Studio"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
    Monitor        "Apple Studio"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection[/LEFT]
  
```
 HTH; post back with other questions.

---

### Post by ghstridr on 2006-08-22
Tried that, black screen again.  I tried runnig dpkg-reconfigure once more, putting the max resolution at 640x480 and made the default color depth 8 bits.  It finally came up and displayed.  As soon as I tried any other resolution or bit depth, black screen again.

---

### Post by avtolle on 2006-08-22
It is a problem with your configuration. OK, if you can get to a command line prompt, type in gksudo gedit /etc/X11/xorg.conf, to edit the file; go to the section for monitor, enter your desired Horizontal Synch and Vertical Refresh values (suggest you use the ones I posted); go to the section for screen, and for each depth, enter your desired resolutions (again, for this purpose, use the ones I posted); then save the file, and restart your computer. Please also check the entries under "Device" to be sure your graphics card and driver are appropriate, before saving the file.

One other suggestion: download the 6.06.1 Alternate Install iso, burn a cd as iso image, and reinstall from there; perhaps the newer kernel on the .1 release will have better drivers. HTH

---

### Post by stmiller on 2006-08-22
Did you try the radeon driver? Try editing the line:

```
Section "Device"
    Driver        "ati"
```

to say 

```
Section "Device"
    Driver        "radeon"
```

---

