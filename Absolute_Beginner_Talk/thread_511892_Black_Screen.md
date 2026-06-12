---
title: "Black Screen"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by skrribble on 2007-07-28
Well.... I'm using Feisty on an older HP desktop that was sitting around and i decided to screw around with... Anyway, I had everything working correctly just the way I wanted, and I decided to pop in an nvidia geforce2 mx 200 video card and see if i could get that working.  Prior to this I had been using the onboard video card.  Once I did this (installed drivers from the REstricted drivers) and rebooted, i got a black screen.  I decided, what the hell I'll just swtich back to the onbaord card and forget about it... However after reconfiguring xorg.conf with 

sudo dpkg-reconfigure xserver-xorg

about six times, I can't get a fix.  Xserver seems to be running and so is gnome.  I've tried restarting each one various times, using different values for the depth, etc.  All I get after the boot up screen is BLACK... I can do CTRL+ALT+F1 to login and do commands from there, but nothing seems to help.

Thank you in advance for anyone with some help!

---

### Post by Pragmatist on 2007-07-28
Did you physically remove the NVIDIA card?  X backs up the xorg.conf file when you run the configurator.  Post your current xorg.conf and see if you can find your original xorg.conf and post it here as well.

---

### Post by skrribble on 2007-07-29
Yes, I physically removed the nvidia card from the mahcine.

Here is my xorg.conf:

```

Section "Files"
             FontPath          "/usr/share/fonts/X11/misc"
             FontPath          "/usr/share/fonts/X11/cyrillic"
             FontPath          "/usr/share/fonts/X11/100dpi/:unscaled"
             FontPath          "/usr/share/fonts/X11/75dpi/:unscaled"
             FontPath          "/usr/share/fonts/X11/Type1"
             FontPath          "/usr/share/fonts/X11/100dpi"
             FontPath          "/usr/share/fonts/X11/75dpi"
             # path to defoma fonts
             FontPath          "/var/lib/defoma/x-ttcidfont-conof.d/dirs/TrueType"
EndSection

Section "Module"
             Load                 "bitmap"
             Load                 "ddc"
             Load                 "dri"
             Load                 "extmod"
             Load                 "freetype"
             Load                 "glx"
             Load                 "int10"
             Load                 "vbe"
EndSection

Section "InputDevice"
             Identifier          "Generic Keyboard"
             Driver              "kbd"
             Option              "CoreKeyboard"
             Option              "XkbRules"         "xorg"
             Option              "XkbModel"         "pc105"
             Option              "XkbLayout"        "us"
EndSection

Section "InputDevice"
             Identifier          "Configured Mouse"
             Driver              "mouse"
             Option              "CorePointer"
             Option              "Device"                           "/dev/input/mice"
             Option              "Protocol"                         "ImPS/2"
             Option              "ZAxisMapping"                     "4 5"
EndSection

Sectioin "InputDevice"
             Driver             "wacom"
             Identifier         "stylus"
             Option             "Device"               "/dev/input/wacom"
             Option             "Type"                 "stylus"
             Option             "ForceDevice"          "ISDV4"                   # Tablet PC ONLY
EndSection

Section "InputDevice"
             Driver             "wacom"
             Identifier         "eraser"
             Option             "Device"               "/dev/input/wacom"
             Option             "Type"                 "eraser"
             Option             "ForceDevice"          "ISDV4"                   # Tablet PC ONLY
EndSection

Section "InputDevice"
             Driver             "wacom"
             Identifier         "cursor"
             Option             "Device"               "/dev/input/wacom"
             Option             "Type"                 "cursor"
             Option             "ForceDevice"          "ISDV4"                   # Tablet PC ONLY
EndSection

Section "Device"
             Identifier         "Onboard Video Card"
             Driver             "vesa"
             BusID              "PCI:0:1:0"
EndSection

Section "Monitor"
             Identifier         "Generic Monitor"
             Option             "DPMS"
             HorizSync          28-49
             VertRefresh        43-72
EndSection

Section "Screen"
             Identifier         "Default Screen"
             Device             "Onboard Video Card"
             Monitor            "Generic Monitor"
             DefaultDepth       24
             SubSection "Display"
                            Depth            1
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display
                            Depth            4
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            Depth            8
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            Depth            15
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            Depth            16
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
EndSection

Section "ServerLayout"
             Identifier      "Default Layout"
             Screen          "Default Screen"
             InputDevice     "Generic Keyboard"
             InputDevice     "Configured Mouse"
             Input Device    "stylus"             "SendCoreEvents"
             InputDevice     "cursor"             "SendCoreEvents"
             InputDevice     "eraser"             "SendCoreEvents"
EndSection

Section "DRI"
             Mode        066
EndSection

```

---

### Post by Pragmatist on 2007-07-29
> 
Section "Screen"
             Identifier         "Default Screen"
             Device             "Onboard Video Card"
             Monitor            "Generic Monitor"
             **DefaultDepth       24**
             SubSection "Display"
                            Depth            1
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display
                            Depth            4
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            Depth            8
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            Depth            15
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            **Depth            16**
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
EndSection


The above section summarizes your screen choices (monitor, video card, resolution)  It also contains "subsections" for video resolution.  The way it is currently, X is looking through the xorg.conf file for a subsection 24 and you don't have one!  You have three choices:

1.) Change the default to a subsection you already have:
```

 Section "Screen"
              Identifier         "Default Screen"
              Device             "Onboard Video Card"
              Monitor            "Generic Monitor"
              [B]DefaultDepth       16
[/B]
```

2.) Add a subsection with depth 24:
```

SubSection "Display"
                            **Depth            24**
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection 

```

3.) Change the depth of one of the existing subsections:
> 
Section "Screen"
             Identifier         "Default Screen"
             Device             "Onboard Video Card"
             Monitor            "Generic Monitor"
             **DefaultDepth       24**
             SubSection "Display"
                            Depth            1
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display
                            Depth            4
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            Depth            8
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            Depth            15
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
             SubSection "Display"
                            **Depth 24**
                            Modes           "1024x768" "800x600" "640x480"
             EndSubSection
EndSection


---

### Post by skrribble on 2007-07-29
OK... the xorg.conf already has that section.... i just missed that subsection when I copied it over from that computer.... sorry... I can be dumb sometimes... i double checked everything else though and tried changing the depth to 16, and it still didnt work... again sorry for the mistake while copying the file

Also when I change the default depth to 16, I get white vertical lines "strobing" randomly all over my screen, kind of like static... this is after i run
```
sudo /etc/init.d/gdm restart
``` to restart gdm

---

### Post by Pragmatist on 2007-07-29
What is the chipset for your onboard video?  You can usually get that by looking up the motherboard online.

Did you find any backed-up copies of the xorg.conf?  Look through the /etc/X11 directory for files containing the word xorg and look through them to see what they use for the video driver.  Is it something other than VESA?

---

### Post by skrribble on 2007-07-29
It appears that the video chipset is Intel 810e on an Asus TUW-AM motherboard.... 

How do I browse through the folder from a command line?  I'm almost positive that it was using the VESA driver before though.

EDIT:  I found the *ls* command and looked thru /etc/X11 and found the back-ups... They all use VESA as the driver.

---

### Post by Pragmatist on 2007-07-29
> **skrribble said:**
> How do I browse through the folder from a command line?
You don't have to use the command line to browse a folder.  If you want to use the command line, you do this:
```
cd /etc/X11; ls -l
```

---

### Post by skrribble on 2007-07-29
all of the old xorg.conf files use the VESA driver...  any ideas?

---

### Post by Pragmatist on 2007-07-29
This is why you always backup an xorg.conf, that you know works, before making any changes to X.

What other differences are there between the files?  Do they all have "generic" monitors?  Are the horizontal and vertical sync rates the same in all files?

Check out this thread:
[http://ubuntuforums.org/showthread.php?p=531943](http://ubuntuforums.org/showthread.php?p=531943)

Other than that, I would do searches using the keyword **intel 810e**  If using google, add the keyword **ubuntu** since that will give you more pertinent results (although you can omit this last keyword if you wish).  On google, this is what I get:
[http://www.google.com/search?hl=en&q=intel+810e+ubuntu&btnG=Search](http://www.google.com/search?hl=en&q=intel+810e+ubuntu&btnG=Search)

---

### Post by skrribble on 2007-07-29
Just to let you know Pragmatist.... I have figured out my situation after some searching.... i reconfigured my xorg one last time, this time using the i810 driver.... restarted the machine and my troubles were gone.....

THANK YOU for all of your help... I really appreciate it, and this community is why Ubuntu may be the best OS out there

---

### Post by rne1223 on 2007-08-03
"Out of Topic": I couldn't agree more, that is why I switch from sabayon to Ubuntu.

---

