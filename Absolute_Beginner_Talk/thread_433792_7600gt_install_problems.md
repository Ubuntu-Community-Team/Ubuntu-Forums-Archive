---
title: "7600gt install problems"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by LiterallyDude on 2007-05-05
My system was running perfectly with Intel GMA 950, then I installed the Nvidia 7600gt and the Nvidia drivers with automatix. 

Here are the problems:
1) Beryl no longer works. 
2) Applying 1440x900 resolution with Nvidia setings manager breaks the display (screen black with mouse arrow).

Here is my xorg.conf:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
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

What should I do next?

Thanks in advance.

---

### Post by robenroute on 2007-05-05
What version of Ubuntu are you running?
Which version/release of the nVidia driver have you got?

---

### Post by LiterallyDude on 2007-05-05
> **robenroute said:**
> What version of Ubuntu are you running?
Which version/release of the nVidia driver have you got?

I am running Feisty and using Nvidia driver version 1.0-9755. Thanks.

---

### Post by RTrev on 2007-05-05
Hi,

Well, I'm running a GeForce 7300 GT which should put us in the same ballpark as far as the driver goes, and I have the same one you do.  I'll tell you my install routine, and maybe it will help.

As installed "out of the box" I was getting about 400 fps from glxgears -info and that wasn't going to do for watching videos and whatnot.

Got the non-free nVidia driver with Synaptic, and while I was there I also decided to try the new low-latency kernel.  I don't think that's related.

I cleaned up my xorg.con so that the following steps would work:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I then ran the following two nvidia-specific commands:

```
sudo nvidia-glx-config enable
sudo nvidia-xconfig --twinview
```

Presumably you can leave out that last one unless you are running dual-head.

Now glxgears -info was showing me a tad over 4000 fps.  Final step:

Edit the /etc/X11/xorg.conf to include the option "Coolbits" "1"

then:

```
sudo nvidia-settings
```

Go to the over-clocking, switch to 3d mode, and let it suggest values to try.  I accepted the suggestions, and now my glxgears -info rating is about 6400 fps.  Good enough.

I hope this helps some!

---

### Post by jaded_pl on 2007-06-20
How did you get those fps numbers? They don't show to me.

---

### Post by RTrev on 2007-06-20
> **jaded_pl said:**
> How did you get those fps numbers? They don't show to me.

Keep  in mind that I have no idea if this is a good benchmark, but I get it by simply opening a terminal and entering:

```

glxgears -info

```

You should see the gears turning, and a ton of information in the terminal.  Just wait.. it will  start printing out single lines telling the FPS.  Or at least mine does.

---

### Post by jaded_pl on 2007-06-20
It does not but works with "glxgears -printfps" - those 6000 you get in windowed mode? (in fulscreen I get less than 1000)

---

### Post by RTrev on 2007-06-20
> **jaded_pl said:**
> It does not but works with "glxgears -printfps" - those 6000 you get in windowed mode? (in fulscreen I get less than 1000)

Here's what happens when I switch in mid-stream to full screen mode:

```

32619 frames in 5.0 seconds = 6523.778 FPS
32344 frames in 5.0 seconds = 6468.633 FPS
--go to full screen here--
2059 frames in 5.0 seconds = 411.682 FPS
2058 frames in 5.0 seconds = 411.585 FPS
2058 frames in 5.0 seconds = 411.505 FPS
2058 frames in 5.0 seconds = 411.586 FPS
2059 frames in 5.0 seconds = 411.602 FPS
2543 frames in 5.0 seconds = 508.587 FPS

```

When I use your syntax, it gives me an error message:

```

bob@ub64:~$ glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
bob@ub64:~$ 

```

Maybe because I'm running dual monitors...

Anyway, I guess this is a good way to measure relative changes in little tweaks we make, but probably isn't a useful benchmark for real-world conditions.  It's just the only one I know of.  :)

---

