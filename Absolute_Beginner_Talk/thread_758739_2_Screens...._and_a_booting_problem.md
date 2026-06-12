---
title: "2 Screens.... and a booting problem"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by mole1012000 on 2008-04-18
I have just installed ubuntu. So far so good BUT my 2nd screen will not register. I know the screens find as i used a 2 screen setup on xp for years.
It just will not "register" on the gui for screens and graphics.

As well sometimes the ubuntu logo hangs on boot and i have to use the gparted live cd a few times to get it to boot. By use i mean just let it load up and then quit without doing anything with it. For whatever reason if i then control+alt+delete, 50% of the time ubuntu will then load.

---

### Post by artblakey on 2008-04-18
Chances are you need to set up your xorg.conf correctly in order to work with both screens and/or graphics cards depending on how you're setup works.

Try reading the info here [http://gentoo-wiki.com/HOWTO_Dual_Monitors]("http://gentoo-wiki.com/HOWTO_Dual_Monitors") and see if it helps you at all. The HOWTO is written for Gentoo, but the basic principles are the same and it's the guide I used when I first set up dual monitors.

I'm assuming you're new to Linux in general and not just Ubuntu, so if a lot of the info in the link doesn't make any sense try posting your current xorg.conf (located at /etc/X11/xorg.conf on your computer) and details of your monitors and graphics card(s) and I'll see if I can help make the changes to the file for you.

---

### Post by herbster on 2008-04-18
It would greatly help if you told us which video card you have and pasted the contents of your xorg.conf:

```
cat /etc/X11/xorg.conf
```

---

### Post by mole1012000 on 2008-04-18
Here is the output from said file. Yes i am very new at this and i am greatful for your help. I have slowly managed to get alot myself but i just didnt know or could find the answer to this!


Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTS]"
        Boardname       "NVIDIA GeForce 8 Series"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
        Vendorname      "NVIDIA"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1440x900"
        Horizsync       31.5-56.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8800 GTS]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1024    768
                Modes           "1024x768@60"   "800x600@60"    "800x600@56"   "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

---

### Post by herbster on 2008-04-18
Okay, nvidia card and the nvidia driver is being used, that's good. You don't have any metamodes, nor Twinview set up, so this should be very simple. Run this from the terminal:

```
sudo nvidia-settings
```

This is my configuration screen, yours will look similar:

[img]http://www.bobgill.net/nvidiasettings.jpg[/img]

All you need to do is select the monitor, set the resolution you want, and in Configure select Twinview. When you've got it set up, you must hit "Save to X Configuration File" at the bottom. This will write your settings to the file you just pasted above.

---

### Post by mole1012000 on 2008-04-18
Thanks guys for your time and in put. It was not smooth sailing. xorg.conf. Killed my install but i managed to fix it through the recovery mode.

Also with regards to my booting issues. I found that i was getting "failed to set xfermode" and the solution for me in this situation. Was to edit a grub line and add irqpoll.

Eg: kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash **irqpoll **

I just thought i would leave a full report. So if anyone else comes across my thread looking for answers. It might just help.

Again cheers.

---

