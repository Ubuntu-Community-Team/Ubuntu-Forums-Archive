---
title: "Screen Res. Help"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by brainiac8008 on 2006-10-15
Hi,
I'm running the Ubuntu 6.06 live cd.  I went to system, preferences, and screen resolution and there was only one option. It's 640*480 at 60 hz.  I went to the terminal (which i'm not too familiar with because i've never really used a command prompt sort of thing before) and put in:

sudo dpkg-reconfigure xserver-xorg

I went through the process and when I got to the screen res. part, every res. I wanted was already selected.  I continued to the end and tried to change my screen res. again.  I was still left with one option:

640*480

Could someone help me?  I'm a complete newbie to Linux so try to explain things clearly.  And if anything can be done visually instead of through the terminal, that would really help. Thanks.

--Noah

---

### Post by igknighted on 2006-10-15
sounds to me like you need to update your graphics driver... The graphics drivers on the Ubuntu live cd don't support my card/monitor and the live cd's dont work.  If you install via the alternate install cd (its not exactly like the live cd installer, but it is roughly the same difficulty of a windows XP install (in other words fairly easy).  Once you get the system installed you can update your graphics drivers (it will be from the command line, but its three easy commands), if you post your graphics card we can tell you how to get the proper drivers

---

### Post by DavidJE13 on 2006-10-15
I had this problem on a computer - the solution is to uncheck all the resolutions appart from the one you want. Don't ask why - it just seems to work ;)

---

### Post by Perfect Storm on 2006-10-15
> **brainiac8008 said:**
> Hi,
I'm running the Ubuntu 6.06 live cd.  I went to system, preferences, and screen resolution and there was only one option. It's 640*480 at 60 hz.  I went to the terminal (which i'm not too familiar with because i've never really used a command prompt sort of thing before) and put in:

sudo dpkg-reconfigure xserver-xorg

I went through the process and when I got to the screen res. part, every res. I wanted was already selected.  I continued to the end and tried to change my screen res. again.  I was still left with one option:

640*480

Could someone help me?  I'm a complete newbie to Linux so try to explain things clearly.  And if anything can be done visually instead of through the terminal, that would really help. Thanks.

--Noah

May we have a look at your xorg.conf?
```
cat /etc/X11/xorg.conf
```

---

### Post by brainiac8008 on 2006-10-15
Sure. How would you look at it though?

--Noah

---

### Post by Perfect Storm on 2006-10-15
just post the output of the command I shown you.

---

### Post by brainiac8008 on 2006-10-15
I can't copy or paste anything. It's too long to type manually.

--Noah

---

### Post by Perfect Storm on 2006-10-15
Okay post: 

Section "Monitor"
Section "Device"
and
Section "Screen"

---

### Post by DavidJE13 on 2006-10-15
Did you try my suggestion? (Using the same sudo- thingie as before, uncheck all the resolutions appart from one) It should definatly fix your problem since it did for me.

---

### Post by brainiac8008 on 2006-10-15
I'll get back to you guys in about 20 minutes.  I have to do something.  I'll be back.

--Noah

---

### Post by bodhi.zazen on 2006-10-15
Try looking at this for some basic information:

[[color=blue]bodhi's resolution solution[/color]](http://ubuntuforums.org/showthread.php?p=1566609#post1566609)

Otherwise Artificial Intelligence is quite knowledgeable. 8-)

---

### Post by alexfittyfives on 2006-10-15
Hi,

```
sudo dpkg-reconfigure xserver-xorg

I went through the process and when I got to the screen res. part, every res. I wanted was already selected. I continued to the end and tried to change my screen res. again. I was still left with one option:
```

Did you restart X after you reconfigured? I think you will need to do this for changes to take effect. One simple way to do this is to hold ctrl, alt and backspace down at the same time (note this will kill your current X session).

---

### Post by brainiac8008 on 2006-10-15
AI,

Here it is:

Section "Device"
Identifier          "NVIDIA Corporation NV18 [GeForce 4 MX - nForce GPU]"
Driver              "nv"
BusID               "PCI:2:0:0"
End Section

Section "Monitor"
Identifier          "F199"
Option              "DPMS"
End Section

Section "Screen"
Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"        Monitor         "F199"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x512" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x512" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x512" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x512" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x512" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x512" "640x480" "640x400"
        EndSubSection
EndSection

I figured out how to copy and paste.  You right-click.

--Noah

---

### Post by brainiac8008 on 2006-10-15
DavidJE13,

I tried what you told me to do but I couldn't figure out how to uncheck something like this [*].  How do you do it?

--Noah

---

### Post by brainiac8008 on 2006-10-15
alexfittyfives,

See, the thing is that everything was already set the way I wanted it to when I first did:

sudo dpkg-reconfigure xserver-xorg

All of the resolutions I wanted were checked.

--Noah

---

### Post by bodhi.zazen on 2006-10-15
Try installing the nvidia driver. See my previous post for the link on how to do that.

If you already installed the nvidia, change> Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce 4 MX - nForce GPU]"
**Driver "nv"**
BusID "PCI:2:0:0"
End Sectionto```
Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce 4 MX - nForce GPU]"
**Driver "nvidia"**
BusID "PCI:2:0:0"
End Section
```

[size=2]*After editing your xorg.conf you need to re-start X*:[/size] [-o<
Use the three finger salute: Ctrl-Alt-Backspace
This will bring you to the log-in screen (GDM).

8-)

---

### Post by DavidJE13 on 2006-10-15
> I tried what you told me to do but I couldn't figure out how to uncheck something like this[*]. How do you do it?

As far as I remember; select it with up/down arrow keys and press space to toggle

---

### Post by brainiac8008 on 2006-10-15
I selected only 1152*824 or something around there for my screen res.  It still doesn't work.  My cat /etc/X11/xorg.conf now looks like this:

ubuntu@ubuntu:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]NVIDIA gforce 4"
        Driver          "nv"
        BusID           "PCI:2:0:0"
        VideoRam        65536
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "F199"
        Option          "DPMS"
        HorizSync       30-68
        VertRefresh     50-85
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]NVIDIA gforce 4"
        Monitor         "F199"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1152x864"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1152x864"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1152x864"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1152x864"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1152x864"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1152x864"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection



What is the problem?!?

--Noah

P.S.  After I chose only one res. once and hit ctrl alt backspace, something went wrong and i went into a sort of black and white terminal without any desktop or anything.  I tried sudo /etc/init.d/gdm start (if that's even what I wanted to do) and it faied.

---

### Post by brainiac8008 on 2006-10-15
Artificial Intelligence, where are you!?!

--Noah

---

### Post by bodhi.zazen on 2006-10-15
You need to install and configure the nvidia drivers...

[Nvidia drivers](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1)

---

### Post by brainiac8008 on 2006-10-15
I tried it and I already have the newest driver.

I'm gonna stop with ubuntu for today.  It's getting annoying that after four hours I can't change the screen resolution.

--Noah

---

### Post by Perfect Storm on 2006-10-15
> **brainiac8008 said:**
> Artificial Intelligence, where are you!?!

--Noah

I do have a life besides computing ;)

```
Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]NVIDIA gforce 4"
Driver "nv"
BusID "PCI:2:0:0"
VideoRam 65536
Option "UseFBDev" "true"
EndSection
```

Change "nv" to "nvidia"
restart X

If it doesn't help, please find you manual to your monitor.
and find where it says:
Horizontal scan range 
Vertical scan range 

please post it.

---

### Post by bodhi.zazen on 2006-10-15
If you installed the new drivers you need to edit xorg.conf like this:

[Edit xorg.conf](http://ubuntuforums.org/showpost.php?p=1619939&postcount=16)

Or just look up ......

ie your problem is you are still using the nv driver as of your last posting of xorg.conf.

AKA when posting.....  Look Down.....

See the section "Manage Attachments"? just attach xorg.conf, it is ever easier then cut and paste and, IMO, keeps the thread easily readable.

---

